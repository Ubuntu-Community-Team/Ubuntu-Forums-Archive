---
title: "Terminal Server Client  Error??"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Absolute Zero on 2006-10-23
Hey all,
    I am using the Terminal Server client to connect to a Windows 2003 Terminal Server and, while I can connect to the terminal server, when a user logs off the terminal server, rdesktop crashes with this error:

NOT IMPLEMENTED System pointer message (0xF700)

I originally had this running on Breezy and thought the error would be corrected by updating to Dapper but to no avail. Any advice??

---

### Post by RedBowers on 2006-10-23
I had the same problem at first and found that switching to RDPv5 solved the errors that I had. Hope this helps.

---

### Post by Absolute Zero on 2006-10-23
Red,
   Thanks for the reply that actually solved the NOT IMPLEMENTED error but now I recieve another one:
An Error Occured
/dev/dsp: Device or resource is busy

--FIX:
After a little searching I discovered that this error was related to sounds, thing is I don't have any audio devices initialized, nor do I plan on having them be as such.  Going under local resources and changing the "Play Sounds" option to "Don't Play" this error was no longer present.

Thanks for you help again Red.

---

### Post by Breathe on 2007-04-21
Hi ubuntu users
I've got the same problem Absolute zero had, i mean

An Error Occured
/dev/dsp: Device or resource is busy

The fix that made it work for you

--FIX:
After a little searching I discovered that this error was related to sounds, thing is I don't have any audio devices initialized, nor do I plan on having them be as such. Going under local resources and changing the "Play Sounds" option to "Don't Play" this error was no longer present.

Doesn't work for me :(  I think i've tried all possible combinations and it doesn't work. It crashes and it reports me the same error

An Error Occured
/dev/dsp: Device or resource is busy

Or it disconnected without any alert

Thank you for your help XD

---

