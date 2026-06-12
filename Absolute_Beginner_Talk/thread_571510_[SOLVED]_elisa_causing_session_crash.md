---
title: "[SOLVED] elisa causing session crash"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by just learning on 2007-10-09
i recently installed elisa through synaptic. and every time i try to use it my whole session crashes and i have to log back in. Anyone have any clues about what that is. thanks in advance:confused:

---

### Post by jfinkels on 2007-10-09
> **just learning said:**
> i recently installed elisa through synaptic. and every time i try to use it my whole session crashes and i have to log back in. Anyone have any clues about what that is. thanks in advance:confused:

Are you using Ubuntu 7.10 Gutsy Gibbon? Is there any error message when you try to start elisa from the terminal by typing:```
elisa
```?

---

### Post by just learning on 2007-10-10
I tried to run it through terminal but as soon as the elisa window comes up it crashes the session so i can't read the errors which there are lots. Yes i am using gutsy Gibbon.

thanks again:???:

---

### Post by just learning on 2007-10-11
I finally got the output from terminal, only because elisa now won't even show a start up window.I will say that at least it doesn't crash the system this is the output in terminal
WARN  MainThread      plugin_registry             Oct 10 23:49:54  Un-met dependency for classic: pgm (elisa/core/plugin_registry.py:195)
WARN  MainThread      plugin_registry             Oct 10 23:49:54  Un-met dependency for coherence_plugin: coherence (elisa/core/plugin_registry.py:195)
WARN  MainThread      plugin_registry             Oct 10 23:49:54  Un-met dependency for flickr_media: twill (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Oct 10 23:49:54  Un-met dependency for bluetooth_input: bluetooth (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Oct 10 23:49:54  Un-met dependency for lirc_input: pylirc (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Oct 10 23:49:54  Un-met dependency for ipod_media: gpod (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Oct 10 23:49:54  Un-met dependency for daap_media: daap (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Oct 10 23:49:54  Un-met dependency for taglib_metadata: tagpy (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Oct 10 23:49:55  Un-met dependency for poblenou: pgm (elisa/core/plugin_registry.py:195)
WARN  MainThread      plugin_registry             Oct 10 23:49:55  Un-met dependency for stage6: BeautifulSoup (elisa/core/plugin_registry.py:195)
WARN  MainThread      plugin_registry             Oct 10 23:49:55  Un-met dependency for weather_pgm_view: pgm (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Oct 10 23:49:55  Plugin 'coherence_plugin' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Oct 10 23:49:55  Component 'coherence_plugin:coherence_service' not found (elisa/core/plugin_registry.py:618)

---

### Post by just learning on 2007-10-11
here is the rest of the output

WARN  MainThread      plugin_registry             Oct 10 23:49:55  Component 'media_good:taglib_metadata' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Oct 10 23:49:56  Plugin 'coherence_plugin' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Oct 10 23:49:56  Component 'coherence_plugin:upnp_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Oct 10 23:49:56  Component 'media_bad:ipod_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Oct 10 23:49:56  Component fspot_media failed to initialize: FSpot DB not found at '/home/greg/.gnome2/f-spot/photos.db' (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Oct 10 23:49:56  Plugin 'stage6' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Oct 10 23:49:56  Component 'stage6:stage_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Oct 10 23:49:56  Component 'flickr:flickr_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Oct 10 23:49:56  Plugin 'poblenou' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      comp_theme_switcher_activity Oct 10 23:49:56  Component 'poblenou:tango_theme' not found (elisa/plugins/good/theme_switcher/theme_switcher_activity.py:56)
WARN  MainThread      plugin_registry             Oct 10 23:49:56  Plugin 'poblenou' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      comp_theme_switcher_activity Oct 10 23:49:56  Component 'poblenou:chris_theme' not found (elisa/plugins/good/theme_switcher/theme_switcher_activity.py:56)
WARN  MainThread      plugin_registry             Oct 10 23:49:56  Plugin 'poblenou' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      comp_theme_switcher_activity Oct 10 23:49:56  Component 'poblenou:poblenou_theme' not found (elisa/plugins/good/theme_switcher/theme_switcher_activity.py:56)
WARN  MainThread      plugin_registry             Oct 10 23:49:57  Plugin 'poblenou' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      comp_theme_switcher_activity Oct 10 23:49:57  Component 'poblenou:tango_theme' not found (elisa/plugins/good/theme_switcher/theme_switcher_activity.py:56)
WARN  MainThread      plugin_registry             Oct 10 23:49:57  Plugin 'poblenou' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      comp_theme_switcher_activity Oct 10 23:49:57  Component 'poblenou:chris_theme' not found (elisa/plugins/good/theme_switcher/theme_switcher_activity.py:56)
WARN  MainThread      plugin_registry             Oct 10 23:49:57  Plugin 'poblenou' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      comp_theme_switcher_activity Oct 10 23:49:57  Component 'poblenou:poblenou_theme' not found (elisa/plugins/good/theme_switcher/theme_switcher_activity.py:56)
WARN  MainThread      plugin_registry             Oct 10 23:49:57  Plugin 'poblenou' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      interface_controller        Oct 10 23:49:57  Cannot create controller 'poblenou:elisa_controller' for backend 'backend1' (elisa/core/interface_controller.py:130)
WARN  MainThread      interface_controller        Oct 10 23:49:57  An error occured causing backend 'backend1' creation to fail (elisa/core/interface_controller.py:75)
A problem occurred in Elisa.
/tmp/elisa_1xMDvI.txt contains the description of this error.
WARN  MainThread      interface_controller        Oct 10 23:49:58  Backend 'backend1' not existing for frontend 'frontend1' (elisa/core/interface_controller.py:165)
WARN  MainThread      interface_controller        Oct 10 23:49:58  An error occured causing frontend 'frontend1' creation to fail (elisa/core/interface_controller.py:90)
A problem occurred in Elisa.
/tmp/elisa_ZYLMjK.txt contains the description of this error.

---

### Post by just learning on 2007-10-14
problem solved when i went back to feisty fawn from gutsy gibbon(i'll wait till the bugs are gone, still learning).

---

