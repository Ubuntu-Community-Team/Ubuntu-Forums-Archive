---
title: "Flash MX + Wine"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Rinku on 2006-09-22
Im not sure if I post this kind of thing here, so bear with me. I installed Flash MX and Adobe Photoshop CS using Wine, everything went perfectly fine, when I try to run either I get this error message with Flash MX:

> fixme: ole:CoRegisterMessageFilter stub
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  172
  Current serial number in output stream:  172

And this with Photoshop CS:

> err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:keyboard:UnregisterHotKey (0x120040,99): stub
fixme:keyboard:RegisterHotKey (0x120040,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x120040,99): stub
fixme:keyboard:RegisterHotKey (0x120040,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x120040,99): stub
fixme:keyboard:RegisterHotKey (0x120040,99,0x00000000,27): stub
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:font:WineEngRemoveFontResourceEx :stub
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  211
  Current serial number in output stream:  211

Can anyone help me?[-o<

---

### Post by madcow72 on 2006-09-22
Curious:  what method did you use to install Flash and CS in wine?  Did you use a particular howto?  I've tried the Howto at: [http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/](http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/)
but have had similar problems...

---

### Post by Rinku on 2006-09-22
> **madcow72 said:**
> Curious:  what method did you use to install Flash and CS in wine?  Did you use a particular howto?  I've tried the Howto at: [http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/](http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/)
but have had similar problems...
Just ran the Setup.exe with Wine directly from Ubuntu, installed, not it opens and crashes. Thats all I did ><

---

