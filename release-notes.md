:robot: I have created a release *beep* *boop*
---


<details><summary>nuxt: 0.13.0</summary>

## [0.13.0](https://github.com/paulkirow/bootstrap-vue-next/compare/nuxt-v0.23.5...nuxt-v0.13.0) (2024-07-15)


### � BREAKING CHANGES

* **BModal:** remove prop backdropVariant
* **BModal:** revert back to using the native `div.modal-backdrop`
* **BOffcanvas:** revert back to native `div.offcanvas-backdrop`
* **BOffcanvas:** remove prop backdropBlur and backdropVariant
* **createBootstrap:** remove automatic import of components and directives fixing an issue with createBootstrap bloating the project size. When components were unused, it bloated the project size -- ie not tree shaking when you only used the plugins
* **createBootstrap:** flatten the params object. The previous "plugins" key is now the top most level object => `{ plugins: { id: {} }` => `{ id: {} }` and so on
* **createBootstrap:** remove alias in createBootstrap, use alias in unplugin-vue-components resolver instead
* remove the default export. Use named export `createBootstrap` instead
* **BOffcanvas:** rename prop backdrop to hideBackdrop to be more in line with standard of bmodal
* remove binputgroupappend binputgroupprepend => use component binputgrouptext
* **BFormInput:** move props lazy, trim & number to v-model modifier. Modifiers should behave more like native Vue modifiers (number modifier with unparseable value returns value as is)
* **BreakpointProps:** strongly type breakpoints. Instead of weak string | number => 1,2,3...'1','2','3'...
* **BDropdown:** replace "container" prop with "teleportTo"
* **BPopover:** replace "container" prop with "teleportTo"
* **BTable:** deprecate noSortReset, use `mustSort`
* **BFormTags:** remove input event -- use https://github.com/update:modelValue
* use createBootstrap function for the plugin definition
* **useBreadcrumb:** return a ref instead of reactive
* **BToast:** rebuild events to match https://getbootstrap.com/docs/5.3/components/toasts/#events (hide, hidden, show, shown)
* **BToast:** close event no longer is start of transition, use "hide" event. Close event now corresponds to when close button is clicked during the hide process
* **BootstrapVuePlugin:** components default is now false. The plugin WILL NOT automatically load all components into global scope (perf) - use option "true" to change
* **BootstrapVuePlugin:** directives default is now false. The plugin WILL NOT automatically load all directives into global scope (perf) - use option "true" to change
* **BootstrapVueNextPlugin:** named export renamed from BootstrapVueNext to BootstrapVueNextPlugin
* rebuild "global variable" system to use app-level provide inject. Review documentation installation guide ([#1719](https://github.com/paulkirow/bootstrap-vue-next/issues/1719))
* **useToast:** redefine the parameters of "show". Instead of many parameters, we simply use a single object
* **useModalController:** redefine the parameters of "show" and "confirm" Instead of many parameters, we simply use a single object
* **useToast:** redefine the parameters of "show". Instead of many p& ([#1712](https://github.com/paulkirow/bootstrap-vue-next/issues/1712))
* required vue 3.4
* rename "Toast" type to OrchestratedToast
* **useToast:** rename "hide" to "remove" to be more in line with useModalController
* **BImg:** rounded none by default
* **BOverlay:** rounded none by default

### Features

* **BCarouselSlide:** allow individual interval for slides ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* **BDropdown:** add teleportDisabled prop ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BDropdown:** replace "container" prop with "teleportTo" ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BFormCheckbox:** use a different value/uncheckedValue system under the hood streamlining the code and process ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BFormInput:** move props lazy, trim & number to v-model modifier. Modifiers should behave more like native Vue modifiers (number modifier with unparseable value returns value as is) ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* **BFormInput:** type number performs the same as modifier ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* **BFormSpinbutton:** remove render functions, fix docs ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BFormTags:** remove input event -- use https://github.com/update:modelValue ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* bimg prop tag ([5e511a6](https://github.com/paulkirow/bootstrap-vue-next/commit/5e511a6a83b2193aa240e1839f1c7a3a3545cae8))
* **BModal:** remove prop backdropVariant ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **BModal:** revert back to using the native `div.modal-backdrop` ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **BOffcanvas:** remove prop backdropBlur and backdropVariant ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **BOffcanvas:** rename prop backdrop to hideBackdrop to be more in line with standard of bmodal ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **BOffcanvas:** revert back to native `div.offcanvas-backdrop` ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **BootstrapVueNextPlugin:** named export renamed from BootstrapVueNext to BootstrapVueNextPlugin ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* **BootstrapVuePlugin:** components default is now false. The plugin WILL NOT automatically load all components into global scope (perf) - use option "true" to change ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* **BootstrapVuePlugin:** directives default is now false. The plugin WILL NOT automatically load all directives into global scope (perf) - use option "true" to change ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* **BPopover:** add teleportDisabled prop ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BPopover:** replace "container" prop with "teleportTo" ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BreakpointProps:** strongly type breakpoints. Instead of weak string | number =&gt; 1,2,3...'1','2','3'... ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* **BTable:** add functional syntax for sortAsc/sortDesc/sortDefault `sortAsc(fieldKey)` to specify the sort content for that specific field ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** add prop multisort ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** allow Numberish values =&gt; string is interpreted as is with maxHeight, numbers are converted to ${number}px maxHeight ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** deprecate noSortReset, use `mustSort` ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** selectedItems becomes a v-modelable prop ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BTable:** WIP fix reactivity engine ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BToaster:** expose show method ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BToast:** I did not eat today and I I have been working for 12 hours straight on this. Enjoy donate at https://opencollective.com/bootstrap-vue-next ([a393473](https://github.com/paulkirow/bootstrap-vue-next/commit/a393473373337e29914d93ace838587e2d829a55))
* **createBootstrap:** flatten the params object. The previous "plugins" key is now the top most level object =&gt; `{ plugins: { id: {} }` => `{ id: {} }` and so on ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **createBootstrap:** remove alias in createBootstrap, use alias in unplugin-vue-components resolver instead ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **createBootstrap:** remove automatic import of components and directives fixing an issue with createBootstrap bloating the project size. When components were unused, it bloated the project size -- ie not tree shaking when you only used the plugins ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* export component prop types ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* implement a use defaults system fixes [#1607](https://github.com/paulkirow/bootstrap-vue-next/issues/1607) ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* implement global alias system fixes [#1753](https://github.com/paulkirow/bootstrap-vue-next/issues/1753) ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* implmenet a use defaults system WIP fixes [#1607](https://github.com/paulkirow/bootstrap-vue-next/issues/1607)  ([#1889](https://github.com/paulkirow/bootstrap-vue-next/issues/1889)) ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* **modalController:** make {} default for show/confirm -- param not required ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **nuxt:** add css option to not automatically include css ([f6adcee](https://github.com/paulkirow/bootstrap-vue-next/commit/f6adceeb2ce4d994215f7864c1adaf39deaa9160))
* **nuxt:** allow passthrough options to createBootstrap plugin ([5458a5a](https://github.com/paulkirow/bootstrap-vue-next/commit/5458a5afd8bb46d3951f3fdee048f85030bc32de))
* **nuxt:** auto import directives ([#1770](https://github.com/paulkirow/bootstrap-vue-next/issues/1770)) ([228e0f7](https://github.com/paulkirow/bootstrap-vue-next/commit/228e0f7a61f92176f4aba78ddd2150dc4467d6cb))
* **nuxt:** automatically globally set teleportTo to `#teleports` ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* **nuxt:** automatically transform asset urls for vite fixes [#1470](https://github.com/paulkirow/bootstrap-vue-next/issues/1470)  ([#1478](https://github.com/paulkirow/bootstrap-vue-next/issues/1478)) ([3b61ee1](https://github.com/paulkirow/bootstrap-vue-next/commit/3b61ee181313a5fb0897b36a89fdb1fed456ef41))
* remove binputgroupappend binputgroupprepend =&gt; use component binputgrouptext ([5e511a6](https://github.com/paulkirow/bootstrap-vue-next/commit/5e511a6a83b2193aa240e1839f1c7a3a3545cae8))
* remove the default export. Use named export `createBootstrap` instead ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* rename "Toast" type to OrchestratedToast ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* required vue 3.4 ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **toast:** make {} default for show -- param not required ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* use createBootstrap function for the plugin definition ([f10fc5f](https://github.com/paulkirow/bootstrap-vue-next/commit/f10fc5f1c3e6305d7c109d92c2c6995178372649))
* **useBreadcrumb:** return a ref instead of reactive ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* **useModalController:** add confirm/show methods to globally create modals ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **useModalController:** add confirm/show methods to globally create modals ([#1701](https://github.com/paulkirow/bootstrap-vue-next/issues/1701)) ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **useModalController:** redefine the parameters of "show" and "confirm" Instead of many parameters, we simply use a single object ([c542416](https://github.com/paulkirow/bootstrap-vue-next/commit/c5424161be549cf11d73af4fca2ef1789ea2a201))
* **useModalController:** show/confirm accept reactive inputs ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **useToast:** redefine the parameters of "show". Instead of many p& ([#1712](https://github.com/paulkirow/bootstrap-vue-next/issues/1712)) ([c542416](https://github.com/paulkirow/bootstrap-vue-next/commit/c5424161be549cf11d73af4fca2ef1789ea2a201))
* **useToast:** redefine the parameters of "show". Instead of many parameters, we simply use a single object ([c542416](https://github.com/paulkirow/bootstrap-vue-next/commit/c5424161be549cf11d73af4fca2ef1789ea2a201))
* **useToast:** rename "hide" to "remove" to be more in line with useModalController ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **useToast:** show to accept reactive inputs ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **utils:** inject getId to allow for custom id generation ([#1836](https://github.com/paulkirow/bootstrap-vue-next/issues/1836)) ([c9e60f5](https://github.com/paulkirow/bootstrap-vue-next/commit/c9e60f57da5ab703a75433a521ebd55eb26ac569))
* WIP table improvements ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))


### Bug Fixes

* BFormRadio use native [@change](https://github.com/change) & [@input](https://github.com/input) events ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BImg:** rounded none by default ([f259f78](https://github.com/paulkirow/bootstrap-vue-next/commit/f259f78cbaef9bb56a813351a64a52c315a56806))
* **BOverlay:** rounded none by default ([f259f78](https://github.com/paulkirow/bootstrap-vue-next/commit/f259f78cbaef9bb56a813351a64a52c315a56806))
* **BTable:** fix handleFieldSorting algorithm to properly handle multisort with mustSort ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** generic types ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** selectModel default value single =&gt; multi ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BTable:** set sort values to undefined so we dont accidentally wipe user defined comparer functions ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** stickyHeader true causes maxHeight 300px ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BToast:** close event no longer is start of transition, use "hide" event. Close event now corresponds to when close button is clicked during the hide process ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* **BToast:** rebuild events to match https://getbootstrap.com/docs/5.3/components/toasts/#events (hide, hidden, show, shown) ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* **Directives:** use TS satisfies over TS as -- surprisingly had an affect ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **generics:** use generic constraints for BTable & BTableLite ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* modal transitions fixes  [#1861](https://github.com/paulkirow/bootstrap-vue-next/issues/1861) ([5e511a6](https://github.com/paulkirow/bootstrap-vue-next/commit/5e511a6a83b2193aa240e1839f1c7a3a3545cae8))
* **nuxt:** defineNuxtPlugin is not defined fixes [#1741](https://github.com/paulkirow/bootstrap-vue-next/issues/1741) ([a5e76d6](https://github.com/paulkirow/bootstrap-vue-next/commit/a5e76d6111d06d3555e6677f128ed9b84af1a66f))
* **nuxt:** do not transformasseturls for img -- Fixed by nuxt ([f259f78](https://github.com/paulkirow/bootstrap-vue-next/commit/f259f78cbaef9bb56a813351a64a52c315a56806))
* **nuxt:** dont teleport everything to #teleports -- selectively teleport based on body fixes [#1898](https://github.com/paulkirow/bootstrap-vue-next/issues/1898) ([e986e94](https://github.com/paulkirow/bootstrap-vue-next/commit/e986e94a7a3db64334ecac6927a7d384cbe5882f))
* **nuxt:** optimize `bootstrap-vue-next` fixes [#1758](https://github.com/paulkirow/bootstrap-vue-next/issues/1758) ([1aba0d1](https://github.com/paulkirow/bootstrap-vue-next/commit/1aba0d1501f815dd7a1a15ed14e874a578d1db9f))
* **nuxt:** resolution of img not working fixes [#1539](https://github.com/paulkirow/bootstrap-vue-next/issues/1539) ([ff63f2c](https://github.com/paulkirow/bootstrap-vue-next/commit/ff63f2c490e3068f61760e5ba59b283c40acedc7))
* rebuild "global variable" system to use app-level provide inject. Review documentation installation guide ([#1719](https://github.com/paulkirow/bootstrap-vue-next/issues/1719)) ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* some migration issues with defineModel ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* Some prop types were build wrong because of vue bug ([3459a54](https://github.com/paulkirow/bootstrap-vue-next/commit/3459a54f4242509a6a23e9a48430de5f3d190157))
* types generation -- use interfaces for componentprops ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* update dependencies to fix a bug in vue compiler ([#1866](https://github.com/paulkirow/bootstrap-vue-next/issues/1866)) ([b2c56bf](https://github.com/paulkirow/bootstrap-vue-next/commit/b2c56bff644177d5653b628a9cbb30ffa5c7055a))
* **useModal:** not working due to registry value not existing when code ran ([f259f78](https://github.com/paulkirow/bootstrap-vue-next/commit/f259f78cbaef9bb56a813351a64a52c315a56806))


### Performance Improvements

* **BTabs:** more efficient unregisterTab function ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **nuxt:** smaller package ([#2012](https://github.com/paulkirow/bootstrap-vue-next/issues/2012)) ([cc1e609](https://github.com/paulkirow/bootstrap-vue-next/commit/cc1e60973b76575fa2cd3ef12ea919fabf152085))
* **useModalManager:** use shallowRef for stack & registry ([f259f78](https://github.com/paulkirow/bootstrap-vue-next/commit/f259f78cbaef9bb56a813351a64a52c315a56806))
* **useToast:** use shallowRef ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))


### Miscellaneous Chores

* release 0.13.0 ([77dfebc](https://github.com/paulkirow/bootstrap-vue-next/commit/77dfebc30d9a3f6f9f990f6128e8405368ffb16a))


### Dependencies

* The following workspace dependencies were updated
  * devDependencies
    * bootstrap-vue-next bumped to 0.13.0
  * peerDependencies
    * bootstrap-vue-next bumped to 0.13.0
</details>

<details><summary>bootstrapvuenext: 0.13.0</summary>

## [0.13.0](https://github.com/paulkirow/bootstrap-vue-next/compare/bootstrapvuenext-v0.23.5...bootstrapvuenext-v0.13.0) (2024-07-15)


### � BREAKING CHANGES

* **BFormFloatingLabel:** remove prop text -- didn't make sense
* **package:** move remainder of dependencies to devDependencies -- if using typescript, you may need to install additional dev dependencies so the types are bundled properly
* **package:** move remainder of dependencies to devDependencies -- if using typescript, you may need to install additional dev dependencies so the types are bundled properly
* **BModal:** remove prop backdropVariant
* **BModal:** revert back to using the native `div.modal-backdrop`
* **BOffcanvas:** revert back to native `div.offcanvas-backdrop`
* **BOffcanvas:** remove prop backdropBlur and backdropVariant
* **createBootstrap:** remove automatic import of components and directives fixing an issue with createBootstrap bloating the project size. When components were unused, it bloated the project size -- ie not tree shaking when you only used the plugins
* **createBootstrap:** flatten the params object. The previous "plugins" key is now the top most level object => `{ plugins: { id: {} }` => `{ id: {} }` and so on
* **createBootstrap:** remove alias in createBootstrap, use alias in unplugin-vue-components resolver instead
* remove the default export. Use named export `createBootstrap` instead
* **BOffcanvas:** rename prop backdrop to hideBackdrop to be more in line with standard of bmodal
* **BTable:** remove selected event -- use @update:selectedItems ([#1962](https://github.com/paulkirow/bootstrap-vue-next/issues/1962))
* remove binputgroupappend binputgroupprepend => use component binputgrouptext
* **BFormFile:** remove props placement and browser
* **BFormFile:** remove unneeded input-group div
* **Bimg:** converge props start, end, & center into single "placement" prop
* **BCardImg:** converge placment props into single "placement" prop. top, bottom, start,end, center => placement
* **BLink:** remove prop append -- vue router deprecation
* **BTable:** remove prop noSortReset, use mustSort ... by default sortability can be reset by clicking (3) times [asc => desc => undefined => asc...]
* **BAvatar:** remove icon prop - use svg in slot if needed
* **BBadge:** revamp, remove prop textIndicator -- use prop placement (bootstrap also says parent elements should have position-relative class... Not sure how much this affects things)
* **BCard:** remove prop overlay, add it into the imgPlacement prop (imgPlacement="overlay")
* **BAvatar:** remove props badgeTop, badgeStart -- use badgePlacement instead
* **BAvatar:** remove prop badgeOffset, no alternative added
* **BFormInput:** move props lazy, trim & number to v-model modifier. Modifiers should behave more like native Vue modifiers (number modifier with unparseable value returns value as is)
* **BreakpointProps:** strongly type breakpoints. Instead of weak string | number => 1,2,3...'1','2','3'...
* **BDropdown:** replace "container" prop with "teleportTo"
* **BPopover:** replace "container" prop with "teleportTo"
* **BTable:** deprecate noSortReset, use `mustSort`
* **BFormTags:** remove input event -- use https://github.com/update:modelValue
* **BFormCheckboxGroup:** BFormCheckboxGroup no longer emits 'change' and 'input' events, listen for 'update:modelValue' instead
* **BRadioGroup:** BRadioGroup no longer emits 'change' and 'input' events, listen for 'update:modelValue' instead
* **BCheckbox:** Implement reverse and without label ([#1825](https://github.com/paulkirow/bootstrap-vue-next/issues/1825))
* **BCollapse:** change open/close to show/hide in expose and slots
* **BDropdown:** change open/close to show/hide in expose and slots
* remove Booleanish type and useBooleanish composable, replace plain boolean type fixes #1774
* use createBootstrap function for the plugin definition
* **BFormCheckbox:** Correct casing of property ariaLabelledby , ariaLabelledBy => ariaLabelledby
* **useBreadcrumb:** return a ref instead of reactive
* **BToast:** rebuild events to match https://getbootstrap.com/docs/5.3/components/toasts/#events (hide, hidden, show, shown)
* **BToast:** close event no longer is start of transition, use "hide" event. Close event now corresponds to when close button is clicked during the hide process
* **BootstrapVuePlugin:** components default is now false. The plugin WILL NOT automatically load all components into global scope (perf) - use option "true" to change
* **BootstrapVuePlugin:** directives default is now false. The plugin WILL NOT automatically load all directives into global scope (perf) - use option "true" to change
* **BootstrapVueNextPlugin:** named export renamed from BootstrapVueNext to BootstrapVueNextPlugin
* rebuild "global variable" system to use app-level provide inject. Review documentation installation guide ([#1719](https://github.com/paulkirow/bootstrap-vue-next/issues/1719))
* **useToast:** redefine the parameters of "show". Instead of many parameters, we simply use a single object
* **useModalController:** redefine the parameters of "show" and "confirm" Instead of many parameters, we simply use a single object
* **useToast:** redefine the parameters of "show". Instead of many p& ([#1712](https://github.com/paulkirow/bootstrap-vue-next/issues/1712))
* **useToast:** redefine the parameters of "show". Instead of many parameters, we simply use a single object
* **useModalController:** redefine the parameters of "show" and "confirm" Instead of many parameters, we simply use a single object
* **useToast:** redefine the parameters of "show" ([#1709](https://github.com/paulkirow/bootstrap-vue-next/issues/1709))
* required vue 3.4
* rename "Toast" type to OrchestratedToast
* **useToast:** rename "hide" to "remove" to be more in line with useModalController
* rename types to be more in line with the standard in vue-router (copying example RouteLocationRaw applies to TableFieldRaw, for example)
* rename TableFieldObject => TableField
* rename TableField => TableFieldRaw
* rename TableFieldObjectFormatter => TableFieldFormatter
* rename SelectOptionObject => SelectOpttion
* rename SelectOption => SelectOptionRaw
* **FormSelect:** fully remove deprecated object options syntax fixes #1593
* rename BreadcrumbItemObject => BreadcrumbItem
* rename BreadcrumbItem => BreadcrumbItemRaw
* rename types to be more in line with the standard in vue-route& ([#1699](https://github.com/paulkirow/bootstrap-vue-next/issues/1699))
* rename BToaster => BToastOrchestrator... This is to make a more generic name that conforms with the new BModalOrchestrator... If other orchestrating components are added, they should use this format as well
* rename BToaster => BToastOrchestrator ([#1697](https://github.com/paulkirow/bootstrap-vue-next/issues/1697))
* **BOffcanvas:** add responsive prop
* **BOffcanvas:** remove lazy prop
* **BTable:** remove b-table-sort-asc && b-table-sort-desc -- use slot sortAsc & sortDesc
* **BTable:** remove automatic selected column when using a selectable table
* **BPopover:** BPopoverPlacement type => PopoverPlacement
* **BDropdown:** remove block prop, note other about BButton -- use the class attr to implement this yourself
* **BButton:** block prop not doing anything -- block prop was REMOVED (making the button display in a block now requires a wrapper element. To make your button display as a block, use a wrapper utility read https://getbootstrap.com/docs/5.3/components/buttons/#block-buttons )
* **BImg:** rounded none by default
* **BOverlay:** rounded none by default
* **BLink:** change the default behavior of blink to not be _self, instead being just undefined
* **BTable:** permanently remove BTable provider "callback" parameter. Callbacks are outdated -- ES2020 target
* **BTable:** permanently remove BTable provider "callback" paramete& ([#1563](https://github.com/paulkirow/bootstrap-vue-next/issues/1563))
* **BAvatar:** badgeLeft => badgeStart
* **BModal:** event emitting for hide event closer to Bootstrap v5 implementation
* **BOffcanvas:** event emitting for hide event closer to Bootstrap v5 implementation
* **BCardBody:** rename prop bodyBgVariant to bgVariant to fit with the expected prop structure
* **BCardBody:** rename prop bodyTextVariant to textVariant to fit with the expected prop structure
* **BCardBody:** rename prop bodyTag to tag to fit with the expected prop structure
* **BCardBody:** rename prop bodyBgVariant to bgVariant to fit with the expected prop structure

### Features

* add Scrollspy composable ([1add107](https://github.com/paulkirow/bootstrap-vue-next/commit/1add107be0b8c045d00dc43a3c9e0443e1c180a2))
* add v-b-scrollspy directive ([1add107](https://github.com/paulkirow/bootstrap-vue-next/commit/1add107be0b8c045d00dc43a3c9e0443e1c180a2))
* **BAccordion:** add class props for elements ([94d5266](https://github.com/paulkirow/bootstrap-vue-next/commit/94d5266d4eb42d54d7ea19e8ed1bb6d6fc4e1cb7))
* **BAvatar:** add prop badgeDotIndicator ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BAvatar:** add prop badgePill ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BAvatar:** remove icon prop - use svg in slot if needed ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BAvatar:** remove prop badgeOffset, no alternative added ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BAvatar:** remove props badgeTop, badgeStart -- use badgePlacement instead ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BAvatar:** size type =&gt; LiteralUnion&lt;Size, Numberish> ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* **BBadge:** add prop placement with directions to place on element ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BBadge:** dotindicator follows placement of prop placement ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BBadge:** revamp, remove prop textIndicator -- use prop placement (bootstrap also says parent elements should have position-relative class... Not sure how much this affects things) ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BBadge:** when dotIndicator is true, use class visually-hidden on text ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BCardImg:** converge placment props into single "placement" prop. top, bottom, start,end, center =&gt; placement ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BCard:** remove prop overlay, add it into the imgPlacement prop (imgPlacement="overlay") ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BCarouselSlide:** allow individual interval for slides ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* **BCheckbox:** Implement reverse and without label ([#1825](https://github.com/paulkirow/bootstrap-vue-next/issues/1825)) ([6c69ff9](https://github.com/paulkirow/bootstrap-vue-next/commit/6c69ff9eea76d6661ca344262231610106170487))
* **BCollapse:** skipAnimation prop ([4a3eb67](https://github.com/paulkirow/bootstrap-vue-next/commit/4a3eb67f19117d9116f782fa865adb9a60471cb2))
* **BDropdown:** add boundaryPadding prop ([efc1ce9](https://github.com/paulkirow/bootstrap-vue-next/commit/efc1ce91ece776e295680f636e44359408b4eeb7))
* **BDropdown:** add keyboard navigation ([3f8c9bf](https://github.com/paulkirow/bootstrap-vue-next/commit/3f8c9bfbc3dc9dc1225886b5be31fb4e8e15ee5a))
* **BDropdown:** add skipWrapper and wrapperClass props ([bb5cdc5](https://github.com/paulkirow/bootstrap-vue-next/commit/bb5cdc5b04a6167a757dccd48fa8d29bcd190468))
* **BDropdown:** add teleportDisabled prop ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BDropdown:** overflow auto and sizing middleware to limit the size to visible viewport ([efc1ce9](https://github.com/paulkirow/bootstrap-vue-next/commit/efc1ce91ece776e295680f636e44359408b4eeb7))
* **BDropdown:** replace "container" prop with "teleportTo" ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BFormCheckbox:** Add 'reverse' property to checkbox and checkboxgroup ([6c69ff9](https://github.com/paulkirow/bootstrap-vue-next/commit/6c69ff9eea76d6661ca344262231610106170487))
* **BFormCheckboxGroup:** BFormCheckboxGroup no longer emits 'change' and 'input' events, listen for 'update:modelValue' instead ([6c69ff9](https://github.com/paulkirow/bootstrap-vue-next/commit/6c69ff9eea76d6661ca344262231610106170487))
* **BFormCheckbox:** Handle no-label case ([6c69ff9](https://github.com/paulkirow/bootstrap-vue-next/commit/6c69ff9eea76d6661ca344262231610106170487))
* **BFormCheckbox:** Implement indeterminate state fixes [#1611](https://github.com/paulkirow/bootstrap-vue-next/issues/1611) ([0908731](https://github.com/paulkirow/bootstrap-vue-next/commit/0908731135ef0f8207c0dd47b84c6494f771b193))
* **BFormCheckBox:** Implements tri-state checkbox ([#1725](https://github.com/paulkirow/bootstrap-vue-next/issues/1725)) ([0908731](https://github.com/paulkirow/bootstrap-vue-next/commit/0908731135ef0f8207c0dd47b84c6494f771b193))
* **BFormCheckbox:** use a different value/uncheckedValue system under the hood streamlining the code and process ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BFormFile:** add option to remove the default button and/or styles ([14534d1](https://github.com/paulkirow/bootstrap-vue-next/commit/14534d1e5529483294dcd3f313866d8fb0d17df0))
* **BFormFile:** add properties placement and browser as in BootstrapVue ([2fe4e69](https://github.com/paulkirow/bootstrap-vue-next/commit/2fe4e69747c0c4b7a8f518d9d8c09fe673d56c72))
* **BFormFloatingLabel:** require default slot ([1c2722a](https://github.com/paulkirow/bootstrap-vue-next/commit/1c2722a5951f1234cdb576fad473ae75c761d150))
* **BFormInput:** move props lazy, trim & number to v-model modifier. Modifiers should behave more like native Vue modifiers (number modifier with unparseable value returns value as is) ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* **BFormInput:** type number performs the same as modifier ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* **BFormSelect:** accept generic value ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* **BFormSelectOption:** accept generic value ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* **BFormSelectOptionGroup:** accept generic value ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* **BFormSpinbutton:** modify locale resolution behavior to take into account global locale state from useRtl" ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* **BFormSpinbutton:** remove render functions, fix docs ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BFormTags:** remove input event -- use https://github.com/update:modelValue ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BFromRow:** Require default slot ([1c2722a](https://github.com/paulkirow/bootstrap-vue-next/commit/1c2722a5951f1234cdb576fad473ae75c761d150))
* bimg prop tag ([5e511a6](https://github.com/paulkirow/bootstrap-vue-next/commit/5e511a6a83b2193aa240e1839f1c7a3a3545cae8))
* **Bimg:** converge props start, end, & center into single "placement" prop ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BInput:** Alias BFormInput to BInput ([6ceeac5](https://github.com/paulkirow/bootstrap-vue-next/commit/6ceeac5ce479ca758308ccf23f5e5df8673fd89b))
* **BLink:** add prop stretched to add class "stretched-link" ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BLink:** remove prop append -- vue router deprecation ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BLink:** use prop replace ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BListGroup:** prop horizontal =&gt; Booleanish | Breakpoint ([c5e7185](https://github.com/paulkirow/bootstrap-vue-next/commit/c5e7185b976fb86b55cd533bf5278dfa63702b7a))
* **BModal:** add bodyClass and bodyAttrs props ([3809a6b](https://github.com/paulkirow/bootstrap-vue-next/commit/3809a6b17ce42588e67cb5443bdcf8285096b30b))
* **BModal:** add focus trapping to modal fixes https://github.com/bootstrap-vue-next/bootstrap-vue-next/ ([ab8b9a0](https://github.com/paulkirow/bootstrap-vue-next/commit/ab8b9a019d14b9db263cfde00ad7efae13dffbe3))
* **BModal:** add prop noStacking fixes https://github.com/bootstrap-vue-next/bootstrap-vue-next/issues/1182 ([ab8b9a0](https://github.com/paulkirow/bootstrap-vue-next/commit/ab8b9a019d14b9db263cfde00ad7efae13dffbe3))
* **BModal:** remove prop backdropVariant ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **BModal:** revert back to using the native `div.modal-backdrop` ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **BNavbar:** autoClose =&gt; Booleanish ([c5e7185](https://github.com/paulkirow/bootstrap-vue-next/commit/c5e7185b976fb86b55cd533bf5278dfa63702b7a))
* **BNavbar:** container =&gt; fluid | Booleanish | Breakpoint ([c5e7185](https://github.com/paulkirow/bootstrap-vue-next/commit/c5e7185b976fb86b55cd533bf5278dfa63702b7a))
* **BNavbar:** toggleable =&gt; Booleanish | Breakpoint ([c5e7185](https://github.com/paulkirow/bootstrap-vue-next/commit/c5e7185b976fb86b55cd533bf5278dfa63702b7a))
* **BOffcanvas:** add prop responsive ([bfe7e85](https://github.com/paulkirow/bootstrap-vue-next/commit/bfe7e85c2afd6dab714099be3a988c27800cc970))
* **BOffcanvas:** add props backdropBlur and shadow to customize the BOverlay instance ([b90e340](https://github.com/paulkirow/bootstrap-vue-next/commit/b90e340fee56798c7315c3b2091ae8e0bc7e6a79))
* **BOffcanvas:** add responsive prop ([82ae5f3](https://github.com/paulkirow/bootstrap-vue-next/commit/82ae5f3090378bc8058c94e6a8e2665795ecf921))
* **BOffcanvas:** adding attrs and class props ([d259701](https://github.com/paulkirow/bootstrap-vue-next/commit/d259701bafcaaa94797683cb15118fd977bff67d))
* **BOffcanvas:** allow specifying a width ([#1903](https://github.com/paulkirow/bootstrap-vue-next/issues/1903)) ([01f87b8](https://github.com/paulkirow/bootstrap-vue-next/commit/01f87b8cecab1c66632d64b1d04c9b36f32dbe67))
* **BOffcanvas:** remove lazy prop ([82ae5f3](https://github.com/paulkirow/bootstrap-vue-next/commit/82ae5f3090378bc8058c94e6a8e2665795ecf921))
* **BOffcanvas:** remove prop backdropBlur and backdropVariant ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **BOffcanvas:** rename prop backdrop to hideBackdrop to be more in line with standard of bmodal ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **BOffcanvas:** revert back to native `div.offcanvas-backdrop` ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **BootstrapVueNextPlugin:** named export renamed from BootstrapVueNext to BootstrapVueNextPlugin ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* **BootstrapVuePlugin:** components default is now false. The plugin WILL NOT automatically load all components into global scope (perf) - use option "true" to change ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* **BootstrapVuePlugin:** directives default is now false. The plugin WILL NOT automatically load all directives into global scope (perf) - use option "true" to change ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* **BPopover:** add boundary prop ([efc1ce9](https://github.com/paulkirow/bootstrap-vue-next/commit/efc1ce91ece776e295680f636e44359408b4eeb7))
* **BPopover:** add boundaryPadding prop ([efc1ce9](https://github.com/paulkirow/bootstrap-vue-next/commit/efc1ce91ece776e295680f636e44359408b4eeb7))
* **BPopover:** add noninteractive prop ([cd8cbec](https://github.com/paulkirow/bootstrap-vue-next/commit/cd8cbecc2dad68022f4cf22045d478b6e5ec48b4))
* **BPopover:** add peristent option to popover ([a195b5d](https://github.com/paulkirow/bootstrap-vue-next/commit/a195b5d1ec8c0f8152740fc285aaa96810909a06))
* **BPopover:** add teleportDisabled prop ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BPopover:** BPopoverPlacement type =&gt; PopoverPlacement ([de66922](https://github.com/paulkirow/bootstrap-vue-next/commit/de66922a855ab64b3487ced181957fd1012c8f12))
* **BPopover:** overflow auto and sizing middleware to limit the size to visible viewport ([efc1ce9](https://github.com/paulkirow/bootstrap-vue-next/commit/efc1ce91ece776e295680f636e44359408b4eeb7))
* **BPopover:** replace "container" prop with "teleportTo" ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BRadioGroup:** BRadioGroup no longer emits 'change' and 'input' events, listen for 'update:modelValue' instead ([6c69ff9](https://github.com/paulkirow/bootstrap-vue-next/commit/6c69ff9eea76d6661ca344262231610106170487))
* **BreakpointProps:** strongly type breakpoints. Instead of weak string | number =&gt; 1,2,3...'1','2','3'... ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* **Btable:** add aria-sort ([7e55550](https://github.com/paulkirow/bootstrap-vue-next/commit/7e555505d6661bd9a494279a03f883210da716e4))
* **BTable:** add change event -- replaces bv `modelValue` see https://github.com/bootstrap-vue-next/bootstrap-vue-next/issues/1775#issuecomment-2100837299 ([00b5e95](https://github.com/paulkirow/bootstrap-vue-next/commit/00b5e9594f66d9f99355af9e3a5a21636b2fde83))
* **BTable:** add functional syntax for sortAsc/sortDesc/sortDefault `sortAsc(fieldKey)` to specify the sort content for that specific field ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** add isrowselected method fixes [#1233](https://github.com/paulkirow/bootstrap-vue-next/issues/1233) ([#1960](https://github.com/paulkirow/bootstrap-vue-next/issues/1960)) ([3f86900](https://github.com/paulkirow/bootstrap-vue-next/commit/3f86900897b5868060f0826c92594afd6fb86505))
* **BTable:** add no-local-sorting prop ([d5b3abb](https://github.com/paulkirow/bootstrap-vue-next/commit/d5b3abbf6a4d9341786c9836ff80da0a89441a72))
* **BTable:** add noSelectOnClick fixes [#1714](https://github.com/paulkirow/bootstrap-vue-next/issues/1714) ([79ad707](https://github.com/paulkirow/bootstrap-vue-next/commit/79ad707bc67c0a36288ff7386232cb154354199b))
* **BTable:** add prop multisort ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** add prop sortCompareLocale ([55f36d7](https://github.com/paulkirow/bootstrap-vue-next/commit/55f36d7d6db6adb858361fef6de1d607e698203d))
* **BTable:** add prop sortCompareOptions ([55f36d7](https://github.com/paulkirow/bootstrap-vue-next/commit/55f36d7d6db6adb858361fef6de1d607e698203d))
* **BTable:** adds the ability to filter by formatter Solves [#1413](https://github.com/paulkirow/bootstrap-vue-next/issues/1413) ([e7130aa](https://github.com/paulkirow/bootstrap-vue-next/commit/e7130aae51adfd108a9d3843bd974513c298ad39))
* **BTable:** Allow dot in sortby key ([08d30ef](https://github.com/paulkirow/bootstrap-vue-next/commit/08d30eff3c1e4f47c1d47d0dbe57ac7a8af63d31))
* **BTable:** allow Numberish values =&gt; string is interpreted as is with maxHeight, numbers are converted to ${number}px maxHeight ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** allow primaryKey dot notation for attribute path ([78b1b32](https://github.com/paulkirow/bootstrap-vue-next/commit/78b1b32c32b773e6f3a786a089c8daf8ac1068dd))
* **BTable:** changes to internal system WIP ([de66922](https://github.com/paulkirow/bootstrap-vue-next/commit/de66922a855ab64b3487ced181957fd1012c8f12))
* **BTable:** changes to internal system WIP ([#1586](https://github.com/paulkirow/bootstrap-vue-next/issues/1586)) ([de66922](https://github.com/paulkirow/bootstrap-vue-next/commit/de66922a855ab64b3487ced181957fd1012c8f12))
* **BTable:** check selection also using primaryKey attribute ([c540889](https://github.com/paulkirow/bootstrap-vue-next/commit/c540889c65b074ac9651a2d39ea519c1cb41dfff))
* **BTable:** deprecate noSortReset, use `mustSort` ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** Enable more sorting options to get closer to BSV parity ([#1771](https://github.com/paulkirow/bootstrap-vue-next/issues/1771)) ([cafb4c4](https://github.com/paulkirow/bootstrap-vue-next/commit/cafb4c4a59fb376fb77c06fa84f5b512e952d891))
* **BTable:** Enable using fromatter function for sortByFormatted ([cafb4c4](https://github.com/paulkirow/bootstrap-vue-next/commit/cafb4c4a59fb376fb77c06fa84f5b512e952d891))
* **BTable:** Implement sortByFormatted ([cafb4c4](https://github.com/paulkirow/bootstrap-vue-next/commit/cafb4c4a59fb376fb77c06fa84f5b512e952d891))
* **BTableLite:** add class to bottom row tr fixes [#1908](https://github.com/paulkirow/bootstrap-vue-next/issues/1908) ([#1987](https://github.com/paulkirow/bootstrap-vue-next/issues/1987)) ([1d745d1](https://github.com/paulkirow/bootstrap-vue-next/commit/1d745d1923c6f2164e2883093d75ca675f65bc3a))
* **BTable:** Make BTable and BTableLite Generic components fixes [#1682](https://github.com/paulkirow/bootstrap-vue-next/issues/1682) ([2b956ca](https://github.com/paulkirow/bootstrap-vue-next/commit/2b956ca9b578b52afb7e53cdfb7ab975984c0712))
* **BTable:** permanently remove BTable provider "callback" paramete& ([#1563](https://github.com/paulkirow/bootstrap-vue-next/issues/1563)) ([c79fdf0](https://github.com/paulkirow/bootstrap-vue-next/commit/c79fdf01f0a78e131da15372bf77b6c9483e494e))
* **BTable:** permanently remove BTable provider "callback" parameter. Callbacks are outdated -- ES2020 target ([c79fdf0](https://github.com/paulkirow/bootstrap-vue-next/commit/c79fdf01f0a78e131da15372bf77b6c9483e494e))
* **BTable:** remove automatic selected column when using a selectable table ([7e55550](https://github.com/paulkirow/bootstrap-vue-next/commit/7e555505d6661bd9a494279a03f883210da716e4))
* **BTable:** remove b-table-sort-asc && b-table-sort-desc -- use slot sortAsc & sortDesc ([7e55550](https://github.com/paulkirow/bootstrap-vue-next/commit/7e555505d6661bd9a494279a03f883210da716e4))
* **BTable:** remove prop noSortReset, use mustSort ... by default sortability can be reset by clicking (3) times [asc =&gt; desc => undefined => asc...] ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BTable:** remove selected event -- use [@update](https://github.com/update):selectedItems ([#1962](https://github.com/paulkirow/bootstrap-vue-next/issues/1962)) ([9350b3d](https://github.com/paulkirow/bootstrap-vue-next/commit/9350b3dc61aa5d1a2b55c3fbe6cc5d64abfadeee))
* **BTable:** selectedItems becomes a v-modelable prop ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BTableSImple:** add prop tableAttrs & tableClasses -- previously could not modify table attributes when isResponsive === true ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BTable:** striped columns ([3ea84f6](https://github.com/paulkirow/bootstrap-vue-next/commit/3ea84f6cc258f6094ea13e856b3eeb3aada54203))
* **BTable:** using head(...) slots will now keep the sorting icons, fixes [#1976](https://github.com/paulkirow/bootstrap-vue-next/issues/1976) ([#1994](https://github.com/paulkirow/bootstrap-vue-next/issues/1994)) ([3098cf2](https://github.com/paulkirow/bootstrap-vue-next/commit/3098cf2ddb40be812e537cbb754499a051672370))
* **BTable:** WIP fix reactivity engine ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BTabs:** add inactive classes, navItem and tab classes. ([22f3466](https://github.com/paulkirow/bootstrap-vue-next/commit/22f346648b7347af42865a740ddcb72cca2b2aed))
* **BTabs:** keyboard navigation ([e8ecdf1](https://github.com/paulkirow/bootstrap-vue-next/commit/e8ecdf1aae254afae4a6eef6c6bed20b3921e1b6))
* **BTabs:** v-model:active-id to monitor/control the tab. ([e8ecdf1](https://github.com/paulkirow/bootstrap-vue-next/commit/e8ecdf1aae254afae4a6eef6c6bed20b3921e1b6))
* **BToaster:** expose show method ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BToast:** I did not eat today and I I have been working for 12 hours straight on this. Enjoy donate at https://opencollective.com/bootstrap-vue-next ([a393473](https://github.com/paulkirow/bootstrap-vue-next/commit/a393473373337e29914d93ace838587e2d829a55))
* **BTooltip:** add prop interactive ([f683df2](https://github.com/paulkirow/bootstrap-vue-next/commit/f683df2422517d0da2ed2156f2e3608c2ed40d84))
* **BTooltip:** add type interfaces for BPopover props ([6dff95a](https://github.com/paulkirow/bootstrap-vue-next/commit/6dff95af11bbb5eb0d5a562ce0b14dd029d70511))
* build on top of [#1474](https://github.com/paulkirow/bootstrap-vue-next/issues/1474) , globally extend multiple components to include textVariant, bgVariant, and basic variant props. Where variant props override bg & text variant props. Variant props use text-bg- classes & bg & text variant props use bg- & text- classes. This allows more control over how you want to develop colors ([0b6595b](https://github.com/paulkirow/bootstrap-vue-next/commit/0b6595b475ba1af0ce6103a72755ccdf4bbdb9e4))
* **createBootstrap:** flatten the params object. The previous "plugins" key is now the top most level object =&gt; `{ plugins: { id: {} }` => `{ id: {} }` and so on ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **createBootstrap:** remove alias in createBootstrap, use alias in unplugin-vue-components resolver instead ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **createBootstrap:** remove automatic import of components and directives fixing an issue with createBootstrap bloating the project size. When components were unused, it bloated the project size -- ie not tree shaking when you only used the plugins ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* **dist:** dont include src files ([bfe7e85](https://github.com/paulkirow/bootstrap-vue-next/commit/bfe7e85c2afd6dab714099be3a988c27800cc970))
* export component prop types ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* export more types fixes [#1585](https://github.com/paulkirow/bootstrap-vue-next/issues/1585) fixes [#1340](https://github.com/paulkirow/bootstrap-vue-next/issues/1340) ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* export plugins from main module ([#1973](https://github.com/paulkirow/bootstrap-vue-next/issues/1973)) ([f79c516](https://github.com/paulkirow/bootstrap-vue-next/commit/f79c5168b7d43df989546fee78e998a0074c0f99))
* export TableFieldRaw, TableField, & TableFieldFormatter ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* expose Toast type ([a2dfbfe](https://github.com/paulkirow/bootstrap-vue-next/commit/a2dfbfefe6e9a2de6a79fc3f0b5737ede39c6f11))
* extend out props rounded to each individual position element - & ([#1555](https://github.com/paulkirow/bootstrap-vue-next/issues/1555)) ([c5e7185](https://github.com/paulkirow/bootstrap-vue-next/commit/c5e7185b976fb86b55cd533bf5278dfa63702b7a))
* extend out props rounded to each individual position element - roundedTop, roundedBottom, roundedStart, roundedEnd. These function as they do in Bootstrap... This affects BOverlay, BImg, BAvatar (& subsequently BAvatarGroup) ([c5e7185](https://github.com/paulkirow/bootstrap-vue-next/commit/c5e7185b976fb86b55cd533bf5278dfa63702b7a))
* **form-input:** add invalid/valid background styles to type='range' fixes [#2026](https://github.com/paulkirow/bootstrap-vue-next/issues/2026) ([cbb41fa](https://github.com/paulkirow/bootstrap-vue-next/commit/cbb41fae2394895ed7f2b088797bab104dfcef99))
* **FormSelect:** fully remove deprecated object options syntax fixes [#1593](https://github.com/paulkirow/bootstrap-vue-next/issues/1593) ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* implement a use defaults system fixes [#1607](https://github.com/paulkirow/bootstrap-vue-next/issues/1607) ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* implement global alias system fixes [#1753](https://github.com/paulkirow/bootstrap-vue-next/issues/1753) ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* implmenet a use defaults system WIP fixes [#1607](https://github.com/paulkirow/bootstrap-vue-next/issues/1607)  ([#1889](https://github.com/paulkirow/bootstrap-vue-next/issues/1889)) ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* **modalController:** make {} default for show/confirm -- param not required ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* move unplugin-vue-components component resolver to main package ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* move unplugin-vue-components component resolver to main package ([#1918](https://github.com/paulkirow/bootstrap-vue-next/issues/1918)) ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **nuxt:** allow passthrough options to createBootstrap plugin ([5458a5a](https://github.com/paulkirow/bootstrap-vue-next/commit/5458a5afd8bb46d3951f3fdee048f85030bc32de))
* **nuxt:** auto import directives ([#1770](https://github.com/paulkirow/bootstrap-vue-next/issues/1770)) ([228e0f7](https://github.com/paulkirow/bootstrap-vue-next/commit/228e0f7a61f92176f4aba78ddd2150dc4467d6cb))
* **nuxt:** automatically globally set teleportTo to `#teleports` ([8e73b17](https://github.com/paulkirow/bootstrap-vue-next/commit/8e73b177051d4403ca7a159e7c11707de15e638c))
* **nuxt:** automatically transform asset urls for vite fixes [#1470](https://github.com/paulkirow/bootstrap-vue-next/issues/1470)  ([#1478](https://github.com/paulkirow/bootstrap-vue-next/issues/1478)) ([3b61ee1](https://github.com/paulkirow/bootstrap-vue-next/commit/3b61ee181313a5fb0897b36a89fdb1fed456ef41))
* **package:** move remainder of dependencies to devDependencies -- if using typescript, you may need to install additional dev dependencies so the types are bundled properly ([dce4774](https://github.com/paulkirow/bootstrap-vue-next/commit/dce47747ae872edca160bd74a50078b33dade54c))
* **package:** move remainder of dependencies to devDependencies -- if using typescript, you may need to install additional dev dependencies so the types are bundled properly ([dce4774](https://github.com/paulkirow/bootstrap-vue-next/commit/dce47747ae872edca160bd74a50078b33dade54c))
* **package:** move vueuse integrations and focus trap to dev dependencies ([bfe7e85](https://github.com/paulkirow/bootstrap-vue-next/commit/bfe7e85c2afd6dab714099be3a988c27800cc970))
* remove binputgroupappend binputgroupprepend =&gt; use component binputgrouptext ([5e511a6](https://github.com/paulkirow/bootstrap-vue-next/commit/5e511a6a83b2193aa240e1839f1c7a3a3545cae8))
* remove Booleanish type and useBooleanish composable, replace plain boolean type fixes [#1774](https://github.com/paulkirow/bootstrap-vue-next/issues/1774) ([d3a51d3](https://github.com/paulkirow/bootstrap-vue-next/commit/d3a51d36266a2c6315c4e117f988dd7746fe8722))
* remove the default export. Use named export `createBootstrap` instead ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* rename "Toast" type to OrchestratedToast ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* rename BreadcrumbItem =&gt; BreadcrumbItemRaw ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* rename BreadcrumbItemObject =&gt; BreadcrumbItem ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* rename BToaster =&gt; BToastOrchestrator ([#1697](https://github.com/paulkirow/bootstrap-vue-next/issues/1697)) ([289391a](https://github.com/paulkirow/bootstrap-vue-next/commit/289391a00e4aa397149ee7c280368800147e9546))
* rename BToaster =&gt; BToastOrchestrator... This is to make a more generic name that conforms with the new BModalOrchestrator... If other orchestrating components are added, they should use this format as well ([289391a](https://github.com/paulkirow/bootstrap-vue-next/commit/289391a00e4aa397149ee7c280368800147e9546))
* rename plugins to namespace out named imports, export 'toast' could be confusing ([c7defef](https://github.com/paulkirow/bootstrap-vue-next/commit/c7defef7240f87c1b39f5827d5521d06cc994d24))
* rename SelectOption =&gt; SelectOptionRaw ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* rename SelectOptionObject =&gt; SelectOpttion ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* rename TableField =&gt; TableFieldRaw ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* rename TableFieldObject =&gt; TableField ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* rename TableFieldObjectFormatter =&gt; TableFieldFormatter ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* rename types to be more in line with the standard in vue-route& ([#1699](https://github.com/paulkirow/bootstrap-vue-next/issues/1699)) ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* rename types to be more in line with the standard in vue-router (copying example RouteLocationRaw applies to TableFieldRaw, for example) ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* required vue 3.4 ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **TableFieldObject:** tdAttr & thAttr =&gt; Record&lt;string, uknown> ([de66922](https://github.com/paulkirow/bootstrap-vue-next/commit/de66922a855ab64b3487ced181957fd1012c8f12))
* **toast:** make {} default for show -- param not required ([1e88b09](https://github.com/paulkirow/bootstrap-vue-next/commit/1e88b09d8992e13948e6f94278c7c51cf4960ec8))
* use Booleanish in more spots ([c5e7185](https://github.com/paulkirow/bootstrap-vue-next/commit/c5e7185b976fb86b55cd533bf5278dfa63702b7a))
* use createBootstrap function for the plugin definition ([f10fc5f](https://github.com/paulkirow/bootstrap-vue-next/commit/f10fc5f1c3e6305d7c109d92c2c6995178372649))
* **useBreadcrumb:** return a ref instead of reactive ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* **useModalController:** add confirm/show methods to globally create modals ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **useModalController:** add confirm/show methods to globally create modals ([#1701](https://github.com/paulkirow/bootstrap-vue-next/issues/1701)) ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **useModalController:** redefine the parameters of "show" and "confirm" Instead of many parameters, we simply use a single object ([c542416](https://github.com/paulkirow/bootstrap-vue-next/commit/c5424161be549cf11d73af4fca2ef1789ea2a201))
* **useModalController:** redefine the parameters of "show" and "confirm" Instead of many parameters, we simply use a single object ([ef391c4](https://github.com/paulkirow/bootstrap-vue-next/commit/ef391c4e23d7bff92c5df90779279c6d3e917836))
* **useModalController:** show/confirm accept reactive inputs ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **useRtl:** implement useRtl composable https://getbootstrap.com/docs/5.3/getting-started/rtl/ ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* **useToast:** add the ability to programatically hide toasts ([6dff95a](https://github.com/paulkirow/bootstrap-vue-next/commit/6dff95af11bbb5eb0d5a562ce0b14dd029d70511))
* **useToast:** redefine the parameters of "show" ([#1709](https://github.com/paulkirow/bootstrap-vue-next/issues/1709)) ([ef391c4](https://github.com/paulkirow/bootstrap-vue-next/commit/ef391c4e23d7bff92c5df90779279c6d3e917836))
* **useToast:** redefine the parameters of "show". Instead of many p& ([#1712](https://github.com/paulkirow/bootstrap-vue-next/issues/1712)) ([c542416](https://github.com/paulkirow/bootstrap-vue-next/commit/c5424161be549cf11d73af4fca2ef1789ea2a201))
* **useToast:** redefine the parameters of "show". Instead of many parameters, we simply use a single object ([c542416](https://github.com/paulkirow/bootstrap-vue-next/commit/c5424161be549cf11d73af4fca2ef1789ea2a201))
* **useToast:** redefine the parameters of "show". Instead of many parameters, we simply use a single object ([ef391c4](https://github.com/paulkirow/bootstrap-vue-next/commit/ef391c4e23d7bff92c5df90779279c6d3e917836))
* **useToast:** rename "hide" to "remove" to be more in line with useModalController ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **useToast:** show to accept reactive inputs ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **utils:** inject getId to allow for custom id generation ([#1836](https://github.com/paulkirow/bootstrap-vue-next/issues/1836)) ([c9e60f5](https://github.com/paulkirow/bootstrap-vue-next/commit/c9e60f57da5ab703a75433a521ebd55eb26ac569))
* WIP table improvements ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))


### Bug Fixes

* **b-tab:** broken computed classes ([#1985](https://github.com/paulkirow/bootstrap-vue-next/issues/1985)) ([4de1325](https://github.com/paulkirow/bootstrap-vue-next/commit/4de1325eefc915794c30eff0f5d9e706b46e1bd5))
* **BAccordionItem:** HTMLAttributes type for attrs props replaced with Record&lt;string, any&gt; -- allows you to pass in anything, instead of being so strict ([960e3b6](https://github.com/paulkirow/bootstrap-vue-next/commit/960e3b6a4b6722f9b2c2ca7668c57a536174ff94))
* **BAvatar:** badgeLeft =&gt; badgeStart ([c5e7185](https://github.com/paulkirow/bootstrap-vue-next/commit/c5e7185b976fb86b55cd533bf5278dfa63702b7a))
* **BAvatar:** replace useToNumber in useAvatarSize composable ([#1760](https://github.com/paulkirow/bootstrap-vue-next/issues/1760)) ([a87c7d0](https://github.com/paulkirow/bootstrap-vue-next/commit/a87c7d091f2bfc6b10947aaa0def9c8e79bbb81c))
* **BAvatar:** use parentdata.square ([c5e7185](https://github.com/paulkirow/bootstrap-vue-next/commit/c5e7185b976fb86b55cd533bf5278dfa63702b7a))
* **BAvatar:** use parentData.square for computedSquare fixes [#1923](https://github.com/paulkirow/bootstrap-vue-next/issues/1923) ([2662758](https://github.com/paulkirow/bootstrap-vue-next/commit/2662758ae9665f70db1bb8ef07e9d4fd4f2c47ba))
* **BBadge:** use text-bg-variant classes for setting badge background and foreground color ([aec73a6](https://github.com/paulkirow/bootstrap-vue-next/commit/aec73a64d22a80938835908388207effde1117f8))
* **BButton:** block prop not doing anything -- block prop was REMOVED (making the button display in a block now requires a wrapper element. To make your button display as a block, use a wrapper utility read https://getbootstrap.com/docs/5.3/components/buttons/#block-buttons ) ([98735bb](https://github.com/paulkirow/bootstrap-vue-next/commit/98735bb1539164ecc14de7d66328684f690c16c1))
* **BCardBody:** rename prop bodyBgVariant to bgVariant to fit with the expected prop structure ([0b6595b](https://github.com/paulkirow/bootstrap-vue-next/commit/0b6595b475ba1af0ce6103a72755ccdf4bbdb9e4))
* **BCardBody:** rename prop bodyBgVariant to bgVariant to fit with the expected prop structure ([0b6595b](https://github.com/paulkirow/bootstrap-vue-next/commit/0b6595b475ba1af0ce6103a72755ccdf4bbdb9e4))
* **BCardBody:** rename prop bodyTag to tag to fit with the expected prop structure ([0b6595b](https://github.com/paulkirow/bootstrap-vue-next/commit/0b6595b475ba1af0ce6103a72755ccdf4bbdb9e4))
* **BCardBody:** rename prop bodyTextVariant to textVariant to fit with the expected prop structure ([0b6595b](https://github.com/paulkirow/bootstrap-vue-next/commit/0b6595b475ba1af0ce6103a72755ccdf4bbdb9e4))
* **BCardBody:** unnecessary "card-body" class when props.overlay is true ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* **BCollapse:** can toggle while animating ([4a3eb67](https://github.com/paulkirow/bootstrap-vue-next/commit/4a3eb67f19117d9116f782fa865adb9a60471cb2))
* **BCollapse:** change open/close to show/hide in expose and slots ([cd7aaf2](https://github.com/paulkirow/bootstrap-vue-next/commit/cd7aaf2eff4da6d57bba487572c9998c5492fd93))
* **BCollapse:** remove unused accordion prop default ([b7acbc7](https://github.com/paulkirow/bootstrap-vue-next/commit/b7acbc75e9f346d19459b37bce292ba0e2d88692))
* **BDropdown:** calculate size after displaying the dropdown. ([#1765](https://github.com/paulkirow/bootstrap-vue-next/issues/1765)) ([9d6478b](https://github.com/paulkirow/bootstrap-vue-next/commit/9d6478b5bdc785c6767375d984fdb43ba42ea061))
* **BDropdown:** change open/close to show/hide in expose and slots ([cd7aaf2](https://github.com/paulkirow/bootstrap-vue-next/commit/cd7aaf2eff4da6d57bba487572c9998c5492fd93))
* **BDropdown:** fix dropup prop ignored ([efc1ce9](https://github.com/paulkirow/bootstrap-vue-next/commit/efc1ce91ece776e295680f636e44359408b4eeb7))
* **BDropdown:** fix wrapper class, skip wrapper in input-group ([bb5cdc5](https://github.com/paulkirow/bootstrap-vue-next/commit/bb5cdc5b04a6167a757dccd48fa8d29bcd190468))
* **BDropdown:** ignore keynav inside form ([#1812](https://github.com/paulkirow/bootstrap-vue-next/issues/1812)) ([584a986](https://github.com/paulkirow/bootstrap-vue-next/commit/584a98676686fad736baae39ea1082d601b90ed6)), closes [#1742](https://github.com/paulkirow/bootstrap-vue-next/issues/1742)
* **BDropdownItem:** attrs inheritance fixes [#1591](https://github.com/paulkirow/bootstrap-vue-next/issues/1591) ([960e3b6](https://github.com/paulkirow/bootstrap-vue-next/commit/960e3b6a4b6722f9b2c2ca7668c57a536174ff94))
* **BDropdownItem:** attrs inheritance fixes [#1591](https://github.com/paulkirow/bootstrap-vue-next/issues/1591) ([#1592](https://github.com/paulkirow/bootstrap-vue-next/issues/1592)) ([960e3b6](https://github.com/paulkirow/bootstrap-vue-next/commit/960e3b6a4b6722f9b2c2ca7668c57a536174ff94))
* **BDropdown:** remove block prop, note other about BButton -- use the class attr to implement this yourself ([98735bb](https://github.com/paulkirow/bootstrap-vue-next/commit/98735bb1539164ecc14de7d66328684f690c16c1))
* **BFormCheckbox:** Correct casing of property ariaLabelledby , ariaLabelledBy =&gt; ariaLabelledby ([0908731](https://github.com/paulkirow/bootstrap-vue-next/commit/0908731135ef0f8207c0dd47b84c6494f771b193))
* **BFormCheckboxGroup:** updates to modelValue being recursive fixes [#1623](https://github.com/paulkirow/bootstrap-vue-next/issues/1623) ([7991073](https://github.com/paulkirow/bootstrap-vue-next/commit/799107302f13f822b8663539b2594196b2aab054))
* **BFormCheckbox:** Handle contextual state == false correctly ([5574745](https://github.com/paulkirow/bootstrap-vue-next/commit/5574745c55b98777ab9b8eaf487364f7fd70b692))
* **BFormCheckbox:** Prevent empty string being cast to true fixes [#1822](https://github.com/paulkirow/bootstrap-vue-next/issues/1822) ([51d7c01](https://github.com/paulkirow/bootstrap-vue-next/commit/51d7c01c71ac8feae76ae934017384d2de27d3f5))
* **BForm:** expose the form so you can programatically submit fixes bootstrap-vue-next[#913](https://github.com/paulkirow/bootstrap-vue-next/issues/913) ([4269fa5](https://github.com/paulkirow/bootstrap-vue-next/commit/4269fa5498820ef134f21656877f02929650543b))
* **BFormFile:** add properties placement and browser as in BootstrapVue ([#1797](https://github.com/paulkirow/bootstrap-vue-next/issues/1797)) ([2fe4e69](https://github.com/paulkirow/bootstrap-vue-next/commit/2fe4e69747c0c4b7a8f518d9d8c09fe673d56c72))
* **BFormFile:** remove props placement and browser ([14534d1](https://github.com/paulkirow/bootstrap-vue-next/commit/14534d1e5529483294dcd3f313866d8fb0d17df0))
* **BFormFile:** remove unneeded input-group div ([14534d1](https://github.com/paulkirow/bootstrap-vue-next/commit/14534d1e5529483294dcd3f313866d8fb0d17df0))
* **BFormFloatingLabel:** remove prop text -- didn't make sense ([1c2722a](https://github.com/paulkirow/bootstrap-vue-next/commit/1c2722a5951f1234cdb576fad473ae75c761d150))
* **BFormGroup:** change labelSrOnly to labelVisuallyHidden as per BS5 ([b4af72f](https://github.com/paulkirow/bootstrap-vue-next/commit/b4af72febfe8d7cd2350530785a16a93dc914810))
* **BFormInput:** value not being updated properly fixes [#693](https://github.com/paulkirow/bootstrap-vue-next/issues/693) fixes [#652](https://github.com/paulkirow/bootstrap-vue-next/issues/652) ([de66922](https://github.com/paulkirow/bootstrap-vue-next/commit/de66922a855ab64b3487ced181957fd1012c8f12))
* BFormRadio use native [@change](https://github.com/change) & [@input](https://github.com/input) events ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BFormSelect:** array of numbers or dates ([#1839](https://github.com/paulkirow/bootstrap-vue-next/issues/1839)) ([6ea7598](https://github.com/paulkirow/bootstrap-vue-next/commit/6ea759874fd41d3da08ae3cafee052e19b3e51e1))
* **BFormSelect:** Create a SelectValue type for consistency ([993599e](https://github.com/paulkirow/bootstrap-vue-next/commit/993599e862461a94124b47a9daa899a7466f52b4))
* **BFormSelect:** restored b-form-select prop fixes [#1739](https://github.com/paulkirow/bootstrap-vue-next/issues/1739) ([2aaed19](https://github.com/paulkirow/bootstrap-vue-next/commit/2aaed191511d8e219583c4fdc6a5af37c4113bac))
* **BFormTags:** dark mode compatibility ([6b1dd1b](https://github.com/paulkirow/bootstrap-vue-next/commit/6b1dd1bcdd10df6afdc9ba2c5776d6839beca30e))
* **BFormTags:** limitTagsText props is not used fixes [#1804](https://github.com/paulkirow/bootstrap-vue-next/issues/1804) ([0ce4174](https://github.com/paulkirow/bootstrap-vue-next/commit/0ce4174061b2bad2935d505641ccf9c02206545e))
* **BFormTextarea:** value not being updated properly fixes [#693](https://github.com/paulkirow/bootstrap-vue-next/issues/693) fixes [#652](https://github.com/paulkirow/bootstrap-vue-next/issues/652) ([de66922](https://github.com/paulkirow/bootstrap-vue-next/commit/de66922a855ab64b3487ced181957fd1012c8f12))
* **BImg:** rounded none by default ([f259f78](https://github.com/paulkirow/bootstrap-vue-next/commit/f259f78cbaef9bb56a813351a64a52c315a56806))
* **BLink:** change the default behavior of blink to not be _self, instead being just undefined ([d2917a5](https://github.com/paulkirow/bootstrap-vue-next/commit/d2917a5a99ea25ae90ba703c03c9dabd6bc6a5ef))
* **BLink:** missing prop, bad class inheritance, other minor changes ([6d47413](https://github.com/paulkirow/bootstrap-vue-next/commit/6d4741300b4e05920f11c15ceead90471e3a514c))
* **BM0dal:** defineExpose of id not reactive ([0591cee](https://github.com/paulkirow/bootstrap-vue-next/commit/0591cee4d7b1cf01c9a9230f84f46a2946dcd912))
* BModal remove aria-labelledby when not present ([6d6acca](https://github.com/paulkirow/bootstrap-vue-next/commit/6d6acca4fe820896657843a9d88c2f494d9fb259))
* **BModal:** active position when prop id changed not working ([4ccf66d](https://github.com/paulkirow/bootstrap-vue-next/commit/4ccf66d95ca28e6a5411739f472ff8652ebf18e4))
* **BModal:** add component to the internal stack during the execution of the setup function if modelValue is true fixes https://github.com/bootstrap-vue-next/bootstrap-vue-next/issues/1919 ([ab8b9a0](https://github.com/paulkirow/bootstrap-vue-next/commit/ab8b9a019d14b9db263cfde00ad7efae13dffbe3))
* **BMOdal:** append transition behavior fixes [#1943](https://github.com/paulkirow/bootstrap-vue-next/issues/1943) ([#1947](https://github.com/paulkirow/bootstrap-vue-next/issues/1947)) ([e10f742](https://github.com/paulkirow/bootstrap-vue-next/commit/e10f7429fee2c59824933469efe3c66747df3be0))
* **BModal:** Ensure modal-open class is always removed ([#1545](https://github.com/paulkirow/bootstrap-vue-next/issues/1545)) ([083d17d](https://github.com/paulkirow/bootstrap-vue-next/commit/083d17d70f211f289f075f60c8eca8b5d82d2cad))
* **BModal:** event emitting for hide event closer to Bootstrap v5 implementation ([06e875e](https://github.com/paulkirow/bootstrap-vue-next/commit/06e875eca6a3a055c65246619ee11ab19ef59be4))
* **BModal:** Fix new modals stacking behind active modals ([6744503](https://github.com/paulkirow/bootstrap-vue-next/commit/6744503ec7206cf52e1945d366e766ff1fce6a50))
* **BModal:** Fix new modals stacking behind active modals fixes [#1516](https://github.com/paulkirow/bootstrap-vue-next/issues/1516) ([6744503](https://github.com/paulkirow/bootstrap-vue-next/commit/6744503ec7206cf52e1945d366e766ff1fce6a50))
* **BModal:** Fix recent regression breaking body scroll locking ([ca0bc3e](https://github.com/paulkirow/bootstrap-vue-next/commit/ca0bc3e6c68811ad2549d0efcabdd06745ed7d6d))
* **BModal:** in coordination with prop noTrap and adding no focus trapping to opened offcanvas, fixes [#1996](https://github.com/paulkirow/bootstrap-vue-next/issues/1996) -&gt; as trap has moved to offcanvas ([28c64c9](https://github.com/paulkirow/bootstrap-vue-next/commit/28c64c9a3df563c95956fa871acd5556d62a2336))
* **BModal:** modal emits show and hide more than once fixes [#1655](https://github.com/paulkirow/bootstrap-vue-next/issues/1655) ([937293f](https://github.com/paulkirow/bootstrap-vue-next/commit/937293f427047afbf56f17884be48a580d26d681))
* **BModal:** okTitle default to OK ([61c64c2](https://github.com/paulkirow/bootstrap-vue-next/commit/61c64c2085b3e94aa9c02661fbff706000c86b1f))
* **BModal:** prop fullscreen =&gt; Booleanish | Breakpoint ([c5e7185](https://github.com/paulkirow/bootstrap-vue-next/commit/c5e7185b976fb86b55cd533bf5278dfa63702b7a))
* **BModal:** scoped slots fixes [#1418](https://github.com/paulkirow/bootstrap-vue-next/issues/1418) ([186e97a](https://github.com/paulkirow/bootstrap-vue-next/commit/186e97a24af88ab5a14d65b6a044590ce45df9a1))
* **BModal:** trigger events on modelValue change ([#1542](https://github.com/paulkirow/bootstrap-vue-next/issues/1542)) ([cf1698c](https://github.com/paulkirow/bootstrap-vue-next/commit/cf1698ca22c9fb9a8a5467038d794988b79c823d))
* **BModal:** use focus trap default of 'window.document.body' fixes 2016 ([28c64c9](https://github.com/paulkirow/bootstrap-vue-next/commit/28c64c9a3df563c95956fa871acd5556d62a2336))
* **BNavForm:** incorrect grid classes causing issues fixes [#1410](https://github.com/paulkirow/bootstrap-vue-next/issues/1410) ([186e97a](https://github.com/paulkirow/bootstrap-vue-next/commit/186e97a24af88ab5a14d65b6a044590ce45df9a1))
* **BOffcanvas:** add focus trapping to offcanvas ([28c64c9](https://github.com/paulkirow/bootstrap-vue-next/commit/28c64c9a3df563c95956fa871acd5556d62a2336))
* **BOffcanvas:** event emitting for hide event closer to Bootstrap v5 implementation ([06e875e](https://github.com/paulkirow/bootstrap-vue-next/commit/06e875eca6a3a055c65246619ee11ab19ef59be4))
* **BOverlay:** fix noWrap ([#1933](https://github.com/paulkirow/bootstrap-vue-next/issues/1933)) ([55672ff](https://github.com/paulkirow/bootstrap-vue-next/commit/55672ff35f1e5e3cb6b046449d9317206943af7f))
* **BOverlay:** fix rounded prop ([a3f7ba9](https://github.com/paulkirow/bootstrap-vue-next/commit/a3f7ba9dfe9331f3adef705a74df65ef07cd6845))
* **BOverlay:** fixes rounded prop [#1578](https://github.com/paulkirow/bootstrap-vue-next/issues/1578) ([#1579](https://github.com/paulkirow/bootstrap-vue-next/issues/1579)) ([a3f7ba9](https://github.com/paulkirow/bootstrap-vue-next/commit/a3f7ba9dfe9331f3adef705a74df65ef07cd6845))
* **BOverlay:** rounded none by default ([f259f78](https://github.com/paulkirow/bootstrap-vue-next/commit/f259f78cbaef9bb56a813351a64a52c315a56806))
* **BPagination:** re-implemented the missing first-page and last-page ([697fb7e](https://github.com/paulkirow/bootstrap-vue-next/commit/697fb7ea769d4ffe7f26ab8b588faf55912b4571))
* **BPlaceholderButton:** pointwer: wait fixes [#1602](https://github.com/paulkirow/bootstrap-vue-next/issues/1602) ([9724aac](https://github.com/paulkirow/bootstrap-vue-next/commit/9724aac227dbd60f7a692e42ff1c6ffdbd9e5153))
* **BPlaceholderCard:** pointer: wait for img ([9724aac](https://github.com/paulkirow/bootstrap-vue-next/commit/9724aac227dbd60f7a692e42ff1c6ffdbd9e5153))
* **BPopover and Btooltip:** Fixes bootstrap-vue-next[#1232](https://github.com/paulkirow/bootstrap-vue-next/issues/1232) - do not create a new app fro each tooltip or popover ([#1837](https://github.com/paulkirow/bootstrap-vue-next/issues/1837)) ([259a5af](https://github.com/paulkirow/bootstrap-vue-next/commit/259a5af283148a754f71468d35bd9e9c2b196f49))
* **BPopover:** default offset has changed in bootstrap css ([a195b5d](https://github.com/paulkirow/bootstrap-vue-next/commit/a195b5d1ec8c0f8152740fc285aaa96810909a06))
* **BPopover:** fix injection out of setup context. ([#1848](https://github.com/paulkirow/bootstrap-vue-next/issues/1848)) ([fe9b46e](https://github.com/paulkirow/bootstrap-vue-next/commit/fe9b46e379d1fc507906bae8692451fb92b9586d))
* **BPopover:** hide not working ([efc1ce9](https://github.com/paulkirow/bootstrap-vue-next/commit/efc1ce91ece776e295680f636e44359408b4eeb7))
* **BScrollspy:** "isObject" check rejects null value ([69a637a](https://github.com/paulkirow/bootstrap-vue-next/commit/69a637adb46cf9f570203407e019bd3e3821ae21))
* **BTab:** aria-labelledby static fixes [#1457](https://github.com/paulkirow/bootstrap-vue-next/issues/1457) ([88fe921](https://github.com/paulkirow/bootstrap-vue-next/commit/88fe9212c81bf23843a157c7b7572179debcfa3a))
* **BTable:** allow for inferred nested objects for items fixes [#1851](https://github.com/paulkirow/bootstrap-vue-next/issues/1851) ([b7a4520](https://github.com/paulkirow/bootstrap-vue-next/commit/b7a4520b32a8054ae43b74a750d1dfd6864f6c84))
* **BTable:** BTable rowDblClicked event not working fixes [#1795](https://github.com/paulkirow/bootstrap-vue-next/issues/1795) ([bf9c8c4](https://github.com/paulkirow/bootstrap-vue-next/commit/bf9c8c4ec2f4a5e4553b13643e928e3183df4051))
* **BTable:** call items provider when provider changes ([de66922](https://github.com/paulkirow/bootstrap-vue-next/commit/de66922a855ab64b3487ced181957fd1012c8f12))
* **BTable:** current page not working causing no pagination fixes [#1613](https://github.com/paulkirow/bootstrap-vue-next/issues/1613) ([9f2ef8b](https://github.com/paulkirow/bootstrap-vue-next/commit/9f2ef8b982e3757044cb9aa6177a3484ca034688))
* **BTable:** do not run provider function when does not use provider ([51a729e](https://github.com/paulkirow/bootstrap-vue-next/commit/51a729e4b36c58566a4f32dd1736b398fc51ca35))
* **BTable:** do not sort on non-sortable items, even during mount procedure ([de66922](https://github.com/paulkirow/bootstrap-vue-next/commit/de66922a855ab64b3487ced181957fd1012c8f12))
* **BTable:** double fetch of provider when using filter fixes [#1635](https://github.com/paulkirow/bootstrap-vue-next/issues/1635) ([37180b3](https://github.com/paulkirow/bootstrap-vue-next/commit/37180b378fbd092be8879026759e3495a77f5b04))
* **BTable:** emitting and listening to hover events ([c5c98c1](https://github.com/paulkirow/bootstrap-vue-next/commit/c5c98c10230b3786b9a4fa6e3f8ba076d565d354))
* **BTable:** emitting and listening to hover events ([#1689](https://github.com/paulkirow/bootstrap-vue-next/issues/1689)) ([c5c98c1](https://github.com/paulkirow/bootstrap-vue-next/commit/c5c98c10230b3786b9a4fa6e3f8ba076d565d354))
* **BTable:** fix handleFieldSorting algorithm to properly handle multisort with mustSort ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** fix reactivity when using mapping ([5e5d3dc](https://github.com/paulkirow/bootstrap-vue-next/commit/5e5d3dce2d24e428e2bf0bec24b45dee799d6d4b))
* **BTable:** fix sort descending and add tests ([cafb4c4](https://github.com/paulkirow/bootstrap-vue-next/commit/cafb4c4a59fb376fb77c06fa84f5b512e952d891))
* **BTable:** fixed aria-sort for th gets changed back to 'none' when no longer sorting ([379b838](https://github.com/paulkirow/bootstrap-vue-next/commit/379b8385fca820ea7c8063867b17a71d44789c5d))
* **BTable:** generic types ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTableLite:** add data-label for fields ([7e55550](https://github.com/paulkirow/bootstrap-vue-next/commit/7e555505d6661bd9a494279a03f883210da716e4))
* **BTableLite:** create clone of items thats used internally to fix toggleDetails flipping -- immutable object does not work with the mutation fixes [#1852](https://github.com/paulkirow/bootstrap-vue-next/issues/1852) ([b7a4520](https://github.com/paulkirow/bootstrap-vue-next/commit/b7a4520b32a8054ae43b74a750d1dfd6864f6c84))
* **BTableLite:** details-showing "undefined" ?? false ([de66922](https://github.com/paulkirow/bootstrap-vue-next/commit/de66922a855ab64b3487ced181957fd1012c8f12))
* **BTableLite:** Pass through table header/footer variant & classes ([3db5218](https://github.com/paulkirow/bootstrap-vue-next/commit/3db5218185044f3a476064eef222b21a57e14491))
* **BTableLite:** slot typo in head for dynamic slot ([341d054](https://github.com/paulkirow/bootstrap-vue-next/commit/341d054aee4729540a84d62659b970380d23bbb9))
* **BTableLite:** value slot scope not using formatItem fixes [#1805](https://github.com/paulkirow/bootstrap-vue-next/issues/1805) ([22039e5](https://github.com/paulkirow/bootstrap-vue-next/commit/22039e52c7300f83f7b30ec7a9f9801df575fe79))
* **btable:** local sort issue ([d5b3abb](https://github.com/paulkirow/bootstrap-vue-next/commit/d5b3abbf6a4d9341786c9836ff80da0a89441a72))
* **BTable:** Pass through original records to slots in most circumstances ([#1869](https://github.com/paulkirow/bootstrap-vue-next/issues/1869)) ([bd5541f](https://github.com/paulkirow/bootstrap-vue-next/commit/bd5541f096e6240c26715d8833561710316f3b69))
* **BTable:** resolve selectAllRows no longer working with provider ([aa86f49](https://github.com/paulkirow/bootstrap-vue-next/commit/aa86f4997fe4a3141c193e24ed92e06417cba61c))
* **BTable:** selectedItems not clearing values properly fixes [#1878](https://github.com/paulkirow/bootstrap-vue-next/issues/1878) ([#1879](https://github.com/paulkirow/bootstrap-vue-next/issues/1879)) ([3b57599](https://github.com/paulkirow/bootstrap-vue-next/commit/3b5759910e640a8f93792b4187082a32cf433015))
* **BTable:** selectedItems with range not displaying class ([3b57599](https://github.com/paulkirow/bootstrap-vue-next/commit/3b5759910e640a8f93792b4187082a32cf433015))
* **BTable:** selectModel default value single =&gt; multi ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **BTable:** set sort values to undefined so we dont accidentally wipe user defined comparer functions ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** sortDesc goes true =&gt; false => undefined so you can now remove a tables sort by just clicking the sort ([7e55550](https://github.com/paulkirow/bootstrap-vue-next/commit/7e555505d6661bd9a494279a03f883210da716e4))
* **BTable:** stickyHeader true causes maxHeight 300px ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **BTable:** tablefield&lt;T&gt; fixes [#2023](https://github.com/paulkirow/bootstrap-vue-next/issues/2023)  ([#2035](https://github.com/paulkirow/bootstrap-vue-next/issues/2035)) ([a5e5cff](https://github.com/paulkirow/bootstrap-vue-next/commit/a5e5cffc12010ca72163491fc49c7f3a31fa788e))
* **BTable:** update:selectedItems Set =&gt; Array (types issue) ([de66922](https://github.com/paulkirow/bootstrap-vue-next/commit/de66922a855ab64b3487ced181957fd1012c8f12))
* **BTabs:** missing aria prop ([e8ecdf1](https://github.com/paulkirow/bootstrap-vue-next/commit/e8ecdf1aae254afae4a6eef6c6bed20b3921e1b6))
* **BTabs:** tabs using provide/inject  ([e8ecdf1](https://github.com/paulkirow/bootstrap-vue-next/commit/e8ecdf1aae254afae4a6eef6c6bed20b3921e1b6))
* **BTab:** use correct buttonId ([#1906](https://github.com/paulkirow/bootstrap-vue-next/issues/1906)) ([2e20c94](https://github.com/paulkirow/bootstrap-vue-next/commit/2e20c94cc7b210fc62126294839b0253b0adfe14))
* **BToast:** close event no longer is start of transition, use "hide" event. Close event now corresponds to when close button is clicked during the hide process ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* **BToast:** rebuild events to match https://getbootstrap.com/docs/5.3/components/toasts/#events (hide, hidden, show, shown) ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* **BToast:** remove autohide property -- use modelValue ([7f6faa9](https://github.com/paulkirow/bootstrap-vue-next/commit/7f6faa929748e96361986a69c5dac47586f5461d))
* **BToast:** remove delay prop fixes [#1638](https://github.com/paulkirow/bootstrap-vue-next/issues/1638) ([b06c4fe](https://github.com/paulkirow/bootstrap-vue-next/commit/b06c4fe25fc625fd9f7a45df9ad3f5bdb5984ce1))
* **BToast:** use headerClass fixes [#1977](https://github.com/paulkirow/bootstrap-vue-next/issues/1977) ([#1978](https://github.com/paulkirow/bootstrap-vue-next/issues/1978)) ([b55583c](https://github.com/paulkirow/bootstrap-vue-next/commit/b55583cee54b1740020ec6cadbe68236cb6dc970))
* **BToggle:** Passing ID as arg or href broken in v0.15 ([553c554](https://github.com/paulkirow/bootstrap-vue-next/commit/553c554b177f2ec013e24526609c725b623de030))
* **BTooltip:** close when opening dropdown, and other changes ([71b5397](https://github.com/paulkirow/bootstrap-vue-next/commit/71b5397609e8f34d4602921d04c8173772525f93))
* **checkbox:** single checkbox not working by default fixes [#1610](https://github.com/paulkirow/bootstrap-vue-next/issues/1610) ([54276ec](https://github.com/paulkirow/bootstrap-vue-next/commit/54276ec4fa98c40280e8df5e291d0b136dd59f31))
* **Directives:** use TS satisfies over TS as -- surprisingly had an affect ([fc1edfb](https://github.com/paulkirow/bootstrap-vue-next/commit/fc1edfb672c665c320618a85b16a90c96c798b8d))
* **events:** update events for BTransition ([c1171d9](https://github.com/paulkirow/bootstrap-vue-next/commit/c1171d94bd1bf429826844aaed39fd360b1d1495))
* further changes to [#1623](https://github.com/paulkirow/bootstrap-vue-next/issues/1623) ([febd812](https://github.com/paulkirow/bootstrap-vue-next/commit/febd81277e538b6926a74f179cc42be7a8fda0bb))
* **generics:** use generic constraints for BTable & BTableLite ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* incorrect classes and placements on bcardimg and bcard ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* modal transitions fixes  [#1861](https://github.com/paulkirow/bootstrap-vue-next/issues/1861) ([5e511a6](https://github.com/paulkirow/bootstrap-vue-next/commit/5e511a6a83b2193aa240e1839f1c7a3a3545cae8))
* **nuxt:** do not transformasseturls for img -- Fixed by nuxt ([f259f78](https://github.com/paulkirow/bootstrap-vue-next/commit/f259f78cbaef9bb56a813351a64a52c315a56806))
* rebuild "global variable" system to use app-level provide inject. Review documentation installation guide ([#1719](https://github.com/paulkirow/bootstrap-vue-next/issues/1719)) ([afd7e5f](https://github.com/paulkirow/bootstrap-vue-next/commit/afd7e5fbd1e8d4decb626c726590225d67804ba1))
* regression from 0.10.8 fixes [#1398](https://github.com/paulkirow/bootstrap-vue-next/issues/1398) ([3e93c5c](https://github.com/paulkirow/bootstrap-vue-next/commit/3e93c5c111307c01f8d40033eb8d9156fcb49fac))
* regression from 0.10.8 fixes [#1398](https://github.com/paulkirow/bootstrap-vue-next/issues/1398)  ([3e93c5c](https://github.com/paulkirow/bootstrap-vue-next/commit/3e93c5c111307c01f8d40033eb8d9156fcb49fac))
* Remove [@input](https://github.com/input) in favor of [@update](https://github.com/update):modelValue fixes [#1657](https://github.com/paulkirow/bootstrap-vue-next/issues/1657) ([aa8bf85](https://github.com/paulkirow/bootstrap-vue-next/commit/aa8bf85960eef92f8b9f7378c29c77b3bc3c3657))
* some migration issues with defineModel ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* Some prop types were build wrong because of vue bug ([3459a54](https://github.com/paulkirow/bootstrap-vue-next/commit/3459a54f4242509a6a23e9a48430de5f3d190157))
* some scoped slots fixes ([fdcb8cd](https://github.com/paulkirow/bootstrap-vue-next/commit/fdcb8cdbdf87f12f98aa13a8071258b586c84bd2))
* **table:** table detail row color when striped fixes [#1716](https://github.com/paulkirow/bootstrap-vue-next/issues/1716) ([8b20f3c](https://github.com/paulkirow/bootstrap-vue-next/commit/8b20f3c1da7887ff8e4d379f677437f95dd694c1))
* types generation -- use interfaces for componentprops ([de60ce3](https://github.com/paulkirow/bootstrap-vue-next/commit/de60ce3cd2bc3ee8768331ae8ce69b2c5f3eed73))
* **types:** mjs masquerading as cjs -- export mts copy ([#1980](https://github.com/paulkirow/bootstrap-vue-next/issues/1980)) ([bfe7e85](https://github.com/paulkirow/bootstrap-vue-next/commit/bfe7e85c2afd6dab714099be3a988c27800cc970))
* update dependencies to fix a bug in vue compiler ([#1866](https://github.com/paulkirow/bootstrap-vue-next/issues/1866)) ([b2c56bf](https://github.com/paulkirow/bootstrap-vue-next/commit/b2c56bff644177d5653b628a9cbb30ffa5c7055a))
* update vueuse fixes [#1937](https://github.com/paulkirow/bootstrap-vue-next/issues/1937) ([6b58a77](https://github.com/paulkirow/bootstrap-vue-next/commit/6b58a771b0d0199c85d81de71de79b805d2f7701))
* use 'floatingStyles' over manual styles ([1773407](https://github.com/paulkirow/bootstrap-vue-next/commit/1773407cb9ccc9d17bc92c1b305ba61e4cfa46bd))
* use esm build of vite ([fb47e98](https://github.com/paulkirow/bootstrap-vue-next/commit/fb47e98317e29f7ef66d148c9bc5ad3451b00c7e))
* useFocusTrap only to run when mounted fixes [#2041](https://github.com/paulkirow/bootstrap-vue-next/issues/2041) ([b72b164](https://github.com/paulkirow/bootstrap-vue-next/commit/b72b164d9a39684bccf33ae4ac489c79d343107c))
* **useModal:** not working due to registry value not existing when code ran ([f259f78](https://github.com/paulkirow/bootstrap-vue-next/commit/f259f78cbaef9bb56a813351a64a52c315a56806))
* **useToast:** global sharing system minor improvements ([d0d9458](https://github.com/paulkirow/bootstrap-vue-next/commit/d0d94586208400170b8e6249e451ebf81d8c857f))


### Performance Improvements

* **BImg:** improve blank img resolution ([84ce349](https://github.com/paulkirow/bootstrap-vue-next/commit/84ce349cf4bbaa5833b1bef4ce67400c0ad783e8))
* **BTable:** remove excess arrays ([7e55550](https://github.com/paulkirow/bootstrap-vue-next/commit/7e555505d6661bd9a494279a03f883210da716e4))
* **BTable:** use Array.some instead of filter().length ([7eed136](https://github.com/paulkirow/bootstrap-vue-next/commit/7eed13632a957824196bc4e37ff3e55951010488))
* **BTabs:** more efficient unregisterTab function ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))
* **nuxt:** smaller package ([#2012](https://github.com/paulkirow/bootstrap-vue-next/issues/2012)) ([cc1e609](https://github.com/paulkirow/bootstrap-vue-next/commit/cc1e60973b76575fa2cd3ef12ea919fabf152085))
* toRef &gt; computed improvements ([0b6595b](https://github.com/paulkirow/bootstrap-vue-next/commit/0b6595b475ba1af0ce6103a72755ccdf4bbdb9e4))
* **useModalManager:** use shallowRef for stack & registry ([f259f78](https://github.com/paulkirow/bootstrap-vue-next/commit/f259f78cbaef9bb56a813351a64a52c315a56806))
* **useToast:** use shallowRef ([ca16a16](https://github.com/paulkirow/bootstrap-vue-next/commit/ca16a168687dc0e17d6dc5c6210205c1911dd793))


### Reverts

* 84ce349 bad update ([cf9b942](https://github.com/paulkirow/bootstrap-vue-next/commit/cf9b94214d704e7462ed8ebadf3891e495fbf1f7))
* changes to blink that broke blink ([8a518a0](https://github.com/paulkirow/bootstrap-vue-next/commit/8a518a00076de22cfa655f08c534e1dacda384b5))
* changes to blink that broke blink ([#1562](https://github.com/paulkirow/bootstrap-vue-next/issues/1562)) ([8a518a0](https://github.com/paulkirow/bootstrap-vue-next/commit/8a518a00076de22cfa655f08c534e1dacda384b5))


### Miscellaneous Chores

* release 0.13.0 ([77dfebc](https://github.com/paulkirow/bootstrap-vue-next/commit/77dfebc30d9a3f6f9f990f6128e8405368ffb16a))
</details>

---
This PR was generated with [Release Please](https://github.com/googleapis/release-please). See [documentation](https://github.com/googleapis/release-please#release-please).