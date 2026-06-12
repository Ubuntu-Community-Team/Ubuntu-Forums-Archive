---
title: "www.onetruemedia.com"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-11-01
Uploading to this website creashes Firefox constantly!  Does anyone else use this?

[www.onetruemedia.com](www.onetruemedia.com)

---

### Post by xyz on 2007-11-01
I just connected to it and everything went fine. Sorry I can't help.

---

### Post by bean77 on 2007-11-01
It works fine until I try to upload.  Then I can upload a picture or movie and it accepts it but then crashes.  When I re-load the page the previous item I uploaded is there.  Weird.  This doesn't happen with any other application and works fine from my husband's laptop.

---

### Post by n3tfury on 2007-11-01
just for kicks try epiphany and/or opera.

---

### Post by philinux on 2007-11-01
Open a terminal and type

firefox -safe-mode

If no problems in this mode then it's one of your addons causing the problem.

---

### Post by bean77 on 2007-11-01
> **n3tfury said:**
> just for kicks try epiphany and/or opera.

Opera doesn't work with it, I'll try Epiphany.

---

### Post by bean77 on 2007-11-01
> **philinux said:**
> Open a terminal and type

firefox -safe-mode

If no problems in this mode then it's one of your addons causing the problem.

So once I have it in safe mode, then what?  I have all of my add-ons disabled.

---

### Post by philinux on 2007-11-01
try uploading

---

### Post by bean77 on 2007-11-01
Did that, still crashed.

Is this something that would warrant a bug report?

---

### Post by philinux on 2007-11-01
ok so its not addons.

Open a terminal and just type firefox and then press enter.

Try the upload and when it crashes make a note of any errors in the terminal and post them.

---

### Post by bean77 on 2007-11-01
Crashed, no message in terminal although last time it said something about a core dump when I went in Safe Mode.  Now I wish I had written it down.

---

### Post by philinux on 2007-11-01
Right well back to the safe mode and copy the error messages this time.

You can use copy and paste in the terminal

---

### Post by bean77 on 2007-11-01
So now in Safe Mode it uploads one or 2 photos and then just hangs.  I've also tried uploading just one at a time and the same thing happens.  No error message in Firefox unless I kill the upload.  This is happening in Galeon too.

This is so strange.

Do you have an account here?  Does it work for you?

---

### Post by bean77 on 2007-11-01
Tried it again, killed the seemingly "stuck" upload, got this message in my terminal:
```

Segmentation fault (core dumped)
```

---

### Post by twiceasworn on 2007-11-01
Oh yay, segmentation fault.  I would say that it is an issue with the coding for that website and it is causing you issues.  That's just my guess though.  Seg Faults usually don't happen because of something a user did.

---

### Post by bean77 on 2007-11-01
> **twiceasworn said:**
> Oh yay, segmentation fault.  I would say that it is an issue with the coding for that website and it is causing you issues.  That's just my guess though.  Seg Faults usually don't happen because of something a user did.

Oh goody!

Sort of.  It works fine with IE from my DH's laptop.  So is this a case where I would write a bug report?

---

### Post by philinux on 2007-11-01
ok

1. Have you got plenty of memory - what you pc spec.

2. Have you got compiz or desktop effects running if so disable them and try again.

I haven't got an account for this site.

Keep going dont give up.

---

### Post by philinux on 2007-11-01
Also which version of firefox is it?

---

### Post by trak87 on 2007-11-01
Here are a few things you can try:

1. Clear the cache

2. Start firefox from the command line and watch the error output when the problem happens.

3. Close Firefox and move or rename your ~/.mozilla directory. You can move it back later. This will cause Firefox to recreate this directory and all your settings so it's a bit like starting Firefox from scratch, but it may solve the problem. If it works just reinstall all your plugins and go from there.

---

