---
title: "Noise reduction tools"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by MickS on 2007-02-15
Please can anyone tell me if there are any Linux equivalents of the NeatImage photo noise reduction software available or a dedicated plugin for the Gimp that would do the job as well.
Thanks
Mick

---

### Post by tronica on 2007-02-15
Heres a plugin for gimp, i havn't tried it, so maybe someone that have will give you some pointers. There is a tutorial on this page


[http://registry.gimp.org/plugin?id=6719]("http://registry.gimp.org/plugin?id=6719")

---

### Post by MickS on 2007-02-15
Ta for that, I have downloaded the plugin just got to work out how to install it in the Gimp now!!!

I had a read of the tutorial but to be honest it just made my brain hurt.

Mick

---

### Post by tronica on 2007-02-15
Sorry about that, its reall easy to install.

First install libgimp2.0-dev

> sudo apt-get install libgimp2.0-dev


then that will include gimptool

so if you donwloaded the plugin to the desktop, cd to the desktop

> cd Desktop

> gimptool --install-script Eg-ISONoiseReduction.scm

then open gimp and go to plugins and search for noise.

---

### Post by MickS on 2007-02-15
Excellent, I followed your instructions and now have the noise plugin installed, funny thing is though it took some finding but it resides in the Script fu menu and is called EG for some reason.
Thanks problem resolved.

Mick

---

### Post by tronica on 2007-02-15
enjoy!

---

### Post by jis on 2007-09-30
I find the plugin very slow. RGB channel blurring works pretty nicely, but I belive I would get better result neutralizing croma noise by Photoshop using Gaussian blur followed by Fade Gaussian Blur with "Color" blending mode. I could not find the fade feature in Gimp, Cinepaint or Krita :(

There are other alternatives in [http://registry.gimp.org/](http://registry.gimp.org/) but you should compile those before use. Anybody tried other noise killers?

---

### Post by potentia on 2007-10-22
You'll need Photoshop and Noise Ninja. Advanced noise reduction is very advanced stuff, and you'll probably have to pay for it.

I have tried so many of the open source programs, and after seconds with Photoshop together with professional plug-ins, then I understand that you can't get everything for free.

---

### Post by ramjet_1953 on 2007-10-22
If you already have a copy of Neat Image Pro, it does work well under WINE.

Regards,
Roger :cool:

---

### Post by unisol on 2008-05-12
where in scriptfu is the isonoise script located? i found it. mine got installed in the filters menu.

---

### Post by antiplex on 2008-07-15
although this thread is a little outdated, i want to share my latest discovery of a beautifully working image denoiser plugin for gimp.
its called '[wavelet denoise]("http://registry.gimp.org/node/4235")' and free (GPL).

installs easily via gimptool-2.0 as described by the author of the plugin.

enjoy!

---

