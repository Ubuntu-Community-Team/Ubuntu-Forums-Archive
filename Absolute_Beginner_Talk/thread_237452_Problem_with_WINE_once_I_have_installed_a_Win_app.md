---
title: "Problem with WINE once I have installed a Win app"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by AndyFrith on 2006-08-16
Pretty much a linux noob here,

Installed Wine and installed Paint Shop Pro from CD with no worries at all from the command line. When I go to run PSP after installing however, I get a splash screen for a split second and then I get this error:

> $ wine "C:\program files\Jasc Software Inc\Paint Shop Pro 7\psp.exe"

fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
err:region:CombineRgn Invalid rgn=(nil)
err:region:CombineRgn Invalid rgn=(nil)
err:region:CombineRgn Invalid rgn=(nil)
err:region:CombineRgn Invalid rgn=(nil)
err:region:CombineRgn Invalid rgn=(nil)
err:region:CombineRgn Invalid rgn=(nil)
err:region:CombineRgn Invalid rgn=(nil)
err:region:CombineRgn Invalid rgn=(nil)
err:region:CombineRgn Invalid rgn=(nil)
err:region:CombineRgn Invalid rgn=(nil)
err:region:CombineRgn Invalid rgn=(nil)
err:region:CombineRgn Invalid rgn=(nil)
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  145 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  640
  Current serial number in output stream:  640

Happens with other programs run in wine also, but only from hard drive it seems. My wine dir is in my home. I did a search for this kind of error, seems to be ubuntu only but as I say I'm clueless.

Many thanks in advance.

---

### Post by jrjr on 2006-08-16
.

---

### Post by AndyFrith on 2006-08-16
Many thanks for the reply, I will check that out when I get a free moment :)

---

