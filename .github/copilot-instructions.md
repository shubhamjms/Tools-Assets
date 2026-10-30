# Public asset release rules

These repository instructions govern versioned tool assets and promotion to the
stable public `prod` folders. Do not reorganize existing assets unless requested.

## Folder roles

- Each tool lives under `vscode-tools\<tool>\`.
- `<tool>\prod\` is the final, stable location used by public image URLs and
  current public documentation. Do not use a version folder as the current
  public endpoint.
- Every new confirmed release gets its own version folder alongside `prod`.
  Use the actual release version and the tool's existing naming convention;
  never invent a version or rename an existing version folder.
- Version folders are change sets, not complete snapshots: include only icons
  and screenshots that changed or were newly added for that release.
- Preserve existing asset subfolder conventions, such as `icons`,
  `feature-icons`, and `screenshots`; do not rename them merely for consistency.

## Preparing a release

1. Confirm the release version, read-only source files, and intended changes.
2. Compare candidate images with the latest approved assets by SHA-256. Do not
   duplicate unchanged images in the new version folder.
3. Give a changed image the same filename and relative asset path it already
   has. Add a new descriptive filename only for a genuinely new image.
4. Add a short public README to each version folder listing changed/new assets
   and which earlier approved version supplies unchanged assets. For a release
   with no image changes, record that fact in the README without copying images.
5. Version-specific documentation must resolve unchanged images to their
   earlier versioned files, not mutable `prod` URLs. Do not assume a change-set
   folder contains every image. Ask if the historical source is unavailable.
6. Preserve previous release folders. Do not overwrite historical assets as
   part of preparing a newer release.

## Promoting approved changes to prod

- Use the newest confirmed release approved by the user for promotion. A newer
  unapproved release must not replace the currently approved public assets.
- Before writing to `prod`, show the release version, exact source/destination
  file list, and whether each image is changed or new. Obtain explicit approval
  for that promotion; preparing a version folder is not production approval.
- Copy only the approved changed/new images into `prod`, retaining their
  filenames and relative asset paths. The promoted bytes must match the
  approved version-folder files.
- Leave unchanged production images untouched. `prod` is the cumulative latest
  approved image set; its images may originate from different release versions.
- Do not update `prod` merely because a release version changed. Update its
  documentation only as needed for approved icon/screenshot changes.
- Keep public URLs stable. Deleting or renaming an existing production image
  requires separate approval because consumers may depend on its URL.

## Safety, validation, and Git

- Publish only approved public PNG images, README documentation, and repository
  instructions. Never copy application source, secrets, credentials, private
  configuration, customer data, VSIX packages, executables, or archives.
- Source extension projects are read-only. Check screenshots for sensitive
  content; stop and request a safe source rather than publishing it.
- Before promotion, verify image hashes, local documentation/image links, and
  the exact changed-file list. Show the proposed commit message.
- Obtain explicit approval before committing or pushing. Production approval
  does not implicitly approve a commit or push, or vice versa.
- Preserve unrelated working-tree and staged changes; stage only task files.
  Never reset or overwrite an existing branch without approval.
- Use normal Git with existing credentials. Do not require GitHub CLI login,
  change global Git/authentication settings, or request tokens in chat.
  Stop and explain any Git authentication failure.
- Never push directly to `main` or bypass branch protection. Creating, approving,
  or merging a pull request, and Marketplace publishing, need separate approval.
- After an approved branch push, verify every newly published or replaced image
  at its public branch URL returns HTTP 200 with PNG content matching its source.
  Do not claim `main` URLs changed before a separately approved merge.
