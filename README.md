# sandstone-server
- store resources in a cache in `resources/.jars`; minecraft server jar, loader, mods
- automatically adds cache to .git/npmignore
- store server configs in `resources/server`
- support handling a server locally (active directory in `.sandstone/server`) 
- support handling a server over SSH (configurable active directory), not for use in a production server
- exports compiled packs, start scripts (including server/loader downloader), mods, & configs to `.sandstone/packs/server.zip`
- hooks with sandstone-cli via the workspace config to provide functionality to `sand build/watch`
- support handling a client locally with the vanilla launcher or a multimc/prism launcher instance, can have dedicated client mods for release, if you're not running a dev server `sand watch` will also attempt to install server files to your client
- exports client modpack as `.mrpack` & mmc instance `.zip` at `.sandstone/packs/client`
- game (server and/or client) is launched attached, printing errors and any messages including `[SANDSTONE-DEBUG]`, automatically running /reload, if resource reloader is installed will automatically run its reload command
- sandstone-cli workflow will serve all files in `.sandstone/packs`, including exports from this library
- sandstone libraries can add mods & configs to be merged by the workspace
- resource manifest is saved at `resources/server/sandstone_manifest.json`, includes static cdn links & file hashes
- CLI at `sand-server/sandstone-server`
  - `setup` prompts you for minecraft version, optional mod loader, optional server setup (either local or SSH info), optional client setup (either userspace vanilla or prism launcher, or MMC folder select)
  - `mod`
    - `list` -> `[{nickname}] {projectPage|'custom'} (src<{cdnLink}>) {?dependency}`
    - `add <modrinth mod_id+file id/slug+file id/file link|curseforge file link|github releases binary link|unknown link|path> <nickname> [target: server|client|both (default: server)]`
    - `update <nickname> <syntax above>`
    - `remove <nickname>`
