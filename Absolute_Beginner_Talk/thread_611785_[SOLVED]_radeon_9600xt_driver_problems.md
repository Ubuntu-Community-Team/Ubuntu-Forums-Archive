---
title: "[SOLVED] radeon 9600xt driver problems"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Nermin on 2007-11-13
hi guys,

as you noticed, i have radeon 9600xt:)
i opened the restricted drivers and checked the ATI accelerated graphics driver
when i restarted afterwards i got a notification that said tha proprietary are being used...

I'm not really sure what that means, do i need other drivers??? and where to get them.
Also, i can't use compiz-fusion. It says:
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

I talk about desktop, and i'm completely new to this. Installed Ubuntu 7.10 yesterday. So, detailed explanation if possible...

---

### Post by mcduck on 2007-11-13
It's telling you that it's using the driver you installed. Restricted Driver Manager installs Ati's own, proprietary, fglrx drivers. So everything is working fine.

What comes to running Compiz with Ati's driver from Ubuntu's repositories, you need to install XGL as well as the driver doesn't support all features needed for Compiz to run. Run 'sudo apt-get install xserver-xgl' (or install that package with Synaptic, if you prefer that way), log out and back again.

---

### Post by Inxsible on 2007-11-13
Also, make sure your card is not blacklisted. I forget the name of the list tho.

Someone who knows might be able to help with the list name

---

### Post by mcduck on 2007-11-13
> **Inxsible said:**
> Also, make sure your card is not blacklisted. I forget the name of the list tho.

Someone who knows might be able to help with the list name

This is only needed if using the latest version of fglrx, from Ati/AMD web site, instead of using the drivers from Ubuntu's repositories. In that case installing XGL would also be unnecessary, but since this is Absolute Beginner forum I would recommend sticking to software available from Ubuntu's repositories..

---

### Post by Nermin on 2007-11-13
wow, i get instant help:)
i thought i would have to wait a day or so for an answer:)
thanks guys:)

ok, now it works, i think at least...

when i type compiz --replace i get the following message:
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

is that good??? :S:S:S

how do i know if compiz works now? what else to do?

---

### Post by Nermin on 2007-11-13
at system preferences i now have advanced desktop effects settings.
So, i guess it works, but please confirm it:)
And, thanks again:)

---

### Post by Inxsible on 2007-11-13
you can press Alt + F2 and type in the command there, then you will not see the terminal messages.

---

### Post by mcduck on 2007-11-13
> **Nermin said:**
> at system preferences i now have advanced desktop effects settings.
So, i guess it works, but please confirm it:)
And, thanks again:)

Well, if you see the effects, it's working ;)

---

### Post by Nermin on 2007-11-13
i guess it works then:)

Thank you again

---

### Post by Inxsible on 2007-11-13
> **Nermin said:**
> i guess it works then:)

Thank you againSweet ! Mark your thread solved. Thread Tools>>Mark thread as solved :)

---

