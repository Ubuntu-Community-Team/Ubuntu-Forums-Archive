---
title: "Installing ATI Drivers"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by jsiii on 2006-02-09
Hello There, I am absolute noob to linux.

I want to make my ATI Radeon work but I have problems installing Ubuntu drivers. I have tried several suggestions but it always led to Xserver corruption so I had to reinstall.

Now I downloaded drivers from ATI and .run file resides on my desktop (ati-driver-installer-8.21.7-x86_64.run). I changed the permissions so that I can execute it but when I double click it, ti says that "I need to run this installer as super user". In the meantime it creates some archive on the disk but after this dialog box, it is deleted.

The display works nice even for greater resolutions, but 3D stuff does not work (it is very slow.)

Can you help me please? Thank you.

---

### Post by Derek Djons on 2006-02-09
Have you tried the ATi drivers which are available through your packetmanager? Note that not all 3D funtionalities of ATi videocards are supported. So achieving 100% performance won't be possible (anyone correct me if I'm wrong).

If you choose to install the ATi drivers from the website you'll have to find out specific information about your monitor such as Vertical / Horizontal Hz. It's not the easiest way if you're new in Linux.

---

### Post by jsiii on 2006-02-09
Hmm, I dont know exactly how to look for them in the packet manager. I have found few, that are already installed but I dont think it is the stuff I am looking for.

Well, I know that the performance will not be like hundred percent but now it looks like 10 percent. Even the simples 3D screensavers have something like 5 fps.

Few how-tos I already tried led me through the process where there was Horizontal and Vertical frequency so I dont think this would be the problem.

And thanks for your reply;-)

**UPDATE:** Hmm, I installed the package: xorg-driver-fglrx with this description: Video driver for the ATI Radeon and FireGL graphics accelerators. This package provides 2D display drivers and hardware accelerated OpenGL... but it seems to have no effect. Do I need to do something else? Was it installed automatically?

---

### Post by cotcot on 2006-02-09
I have used this  : [http://www.student.dtu.dk/~s971652/ati_radeon.shtml](http://www.student.dtu.dk/~s971652/ati_radeon.shtml) .

I had to accelerate my ATI in order to be able to run flightgear.

---

### Post by jsiii on 2006-02-09
After following this tutorial, xserver crashed. There was some Duplicate Symbol error (???)

---

### Post by jsiii on 2006-02-09
\\:D/ \\:D/ \\:D/ \\:D/ \\:D/ 
**Problem solved**

I had to mention that I am using AMD64 architecture. The thread that finally solved my problem is [here]("http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ati+amd64+downgrade")

I had to downgrade the libdri.a file...

COOOOL, I can play Neverball now ;-)

---

