---
title: "Problems running Elisa"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by morwyn on 2007-06-27
When I run Elisa the menu pops up and quickly the program ends.... If I run it in terminal, this is my output: 

```
27/06/2007 16:43:57.627  INFO     Using config file : /home/morwyn/.elisa/./elisa.conf
27/06/2007 16:43:57.836  INFO     Loaded the plugin 'services'
27/06/2007 16:43:57.841  INFO     Loaded the plugin 'pictures'
27/06/2007 16:43:57.843  INFO     Loaded the plugin 'dvd'
27/06/2007 16:43:57.844  INFO     Loaded the plugin 'music'
27/06/2007 16:43:57.858  INFO     Loaded the plugin 'movies'
27/06/2007 16:43:57.861  INFO     Loaded the plugin 'ipod'
27/06/2007 16:43:57.915  INFO     MetaFS plugin won't work without the media manager
27/06/2007 16:43:57.924  INFO     Un-loading meta_fs
27/06/2007 16:43:57.924  INFO     Loaded the plugin 'meta_fs'
27/06/2007 16:43:58.55   INFO     Loaded the plugin 'daap_fs'
27/06/2007 16:43:58.78   INFO     Loaded the plugin 'local_fs'
27/06/2007 16:43:58.235  INFO     Loaded the plugin 'flickr'
27/06/2007 16:43:58.239  INFO     Loaded the plugin 'vfs'
27/06/2007 16:43:58.242  INFO     Loaded the plugin 'upnp'
27/06/2007 16:43:58.243  INFO     Plugins not found : meta_fs
27/06/2007 16:43:58.459  INFO     Loaded the plugin 'weather'
27/06/2007 16:43:58.590  INFO     Loaded the plugin 'config'
27/06/2007 16:43:58.694  INFO     Loaded the plugin 'hal'
27/06/2007 16:43:58.852  INFO     Loaded the plugin 'upnp_server'
27/06/2007 16:43:59.4    INFO     Loaded the plugin 'web_radio'
27/06/2007 16:43:59.5    INFO     Loaded the plugin 'upnp_renderer'
27/06/2007 16:43:59.6    INFO     Loaded the plugin 'http_server'
27/06/2007 16:43:59.10   INFO     [lastfm] Adding location  'lastfm://globaltags/rock'
27/06/2007 16:43:59.11   INFO     [lastfm] Adding location  'lastfm://globaltags/rock'
27/06/2007 16:43:59.23   INFO     No data access plugin found for : lastfm://globaltags/rock
27/06/2007 16:43:59.23   INFO     [lastfm] Adding location  'lastfm://globaltags/jazz'
27/06/2007 16:43:59.25   INFO     No data access plugin found for : lastfm://globaltags/jazz
27/06/2007 16:43:59.27   INFO     [lastfm] Adding location  'lastfm://globaltags/rock'
27/06/2007 16:43:59.86   INFO     No data access plugin found for : lastfm://globaltags/rock
27/06/2007 16:43:59.87   INFO     [lastfm] Adding location  'lastfm://globaltags/jazz'
27/06/2007 16:43:59.89   INFO     No data access plugin found for : lastfm://globaltags/jazz
27/06/2007 16:43:59.106  INFO     [music] Adding location  'meta://artist:list'
27/06/2007 16:43:59.107  INFO     No data access plugin found for : meta://artist:list
27/06/2007 16:43:59.108  INFO     [music] Adding location  'meta://artist:list'
27/06/2007 16:43:59.108  INFO     No data access plugin found for : meta://artist:list
27/06/2007 16:43:59.110  INFO     [lastfm] Adding location  'lastfm://globaltags/jazz'
27/06/2007 16:43:59.111  INFO     Loaded the plugin 'lastfm'
27/06/2007 16:43:59.190  INFO     Using LIRC config file: /usr/lib/python2.4/site-packages/elisa/core/plugins/data/streamzap.lirc
27/06/2007 16:43:59.190  INFO     Loaded the plugin 'lirc'
27/06/2007 16:43:59.198  INFO     Loaded the plugin 'audioscrobbler'
27/06/2007 16:43:59.356  INFO     [music] Adding location  'meta://artist:list'
27/06/2007 16:43:59.357  INFO     No data access plugin found for : meta://artist:list
27/06/2007 16:43:59.358  INFO     libgpod not found. Check out CVS snapshot at http://www.gtkpod.org/libgpod.html
27/06/2007 16:43:59.359  INFO     Un-loading ipod
27/06/2007 16:43:59.452  INFO     Un-loading web_radio
27/06/2007 16:43:59.456  INFO     Please configure your Last.FM account settings
27/06/2007 16:43:59.456  INFO     Un-loading audioscrobbler
 --- Pigment OpenGL status ------------------------
 Version:  2.1.1 NVIDIA 100.14.09
 Renderer: GeForce FX 5500/PCI/SSE2
 Vendor:   NVIDIA Corporation
 GLSL shaders: .............. Yes (used)
 Per YUV component rendering: Yes (used)
 Texture rectangle: ......... Yes (not implemented)
 Fragment program: .......... Yes (not implemented)
 Pixel buffer object: ....... Yes (not implemented)
 --------------------------------------------------
27/06/2007 16:44:02.190  INFO     Loaded the plugin 'default_skin'
27/06/2007 16:44:02.191  INFO     1 skins loaded
27/06/2007 16:44:02.191  INFO     Loading skin default_skin
27/06/2007 16:44:02.343  INFO     Loaded the plugin 'smart_queue'
27/06/2007 16:44:02.343  INFO     Loaded the plugin 'default_queue'
2007/06/27 16:44 -0500 [-] Log opened.
2007/06/27 16:44 -0500 [-] Coherence: Coherence UPnP framework version 0.2.1 starting...
2007/06/27 16:44 -0500 [-] coherence.upnp.core.ssdp.SSDPServer starting on 1900
2007/06/27 16:44 -0500 [-] Starting protocol <coherence.upnp.core.ssdp.SSDPServer instance at 0x860f66c>
2007/06/27 16:44 -0500 [-] coherence.upnp.core.msearch.MSearch starting on 33011
2007/06/27 16:44 -0500 [-] Starting protocol <coherence.upnp.core.msearch.MSearch instance at 0x925958c>
2007/06/27 16:44 -0500 [-] Coherence: running on host: 127.0.1.1
2007/06/27 16:44 -0500 [-] coherence.upnp.core.utils.Site starting on 42683
2007/06/27 16:44 -0500 [-] Coherence: WebServer on port 42683 ready
2007/06/27 16:44 -0500 [-] ControlPoint: Coherence UPnP ControlPoint starting...
2007/06/27 16:44 -0500 [-] Event: EventServer ready...
Traceback (most recent call last):
  File "/usr/bin/elisa", line 7, in ?
    sys.exit(
  File "/usr/lib/python2.4/site-packages/elisa/core/application.py", line 499, in start
    app.run(reactor.loop)
  File "/usr/lib/python2.4/site-packages/elisa/core/application.py", line 366, in run
    application_started.emit()
  File "/usr/lib/python2.4/site-packages/pgm/message/signal.py", line 97, in emit
    receiver(*data, **kw)
  File "/usr/lib/python2.4/site-packages/elisa/core/plugins/hal.py", line 214, in application_started
    self._monitor.detect_coldplugged()
  File "/usr/lib/python2.4/site-packages/elisa/core/plugins/hal.py", line 73, in detect_coldplugged
    self.device_property_modified(len(properties), properties, udi=udi)
  File "/usr/lib/python2.4/site-packages/elisa/core/plugins/hal.py", line 179, in device_property_modified
    name, fstype, unset = self._hotplugged_devices[udi]
KeyError: dbus.String(u'/org/freedesktop/Hal/devices/volume_uuid_3068_8EBA')
Traceback (most recent call last):
  File "logging/handlers.py", line 73, in emit
  File "logging/handlers.py", line 147, in shouldRollover
ValueError: I/O operation on closed file
27/06/2007 16:44:03.503  INFO     Downloading update info
Traceback (most recent call last):
  File "logging/handlers.py", line 73, in emit
  File "logging/handlers.py", line 147, in shouldRollover
ValueError: I/O operation on closed file
27/06/2007 16:44:04.745  INFO     No new update available

```

Could someone suggest to me what I should try to do?

---

### Post by Badjaccur on 2008-01-12
See if someone has the same problem as you or ask your question at [the Elisa forum]("http://elisa.fluendo.com/forums/") :wink:

---

