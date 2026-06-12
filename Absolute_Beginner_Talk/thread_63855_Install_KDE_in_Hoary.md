---
title: "Install KDE in Hoary"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by rajsarkar on 2005-09-09
Hi friends,

I don't have internet connection where in my linux box. Managed to get KDE 3.4.2 package from KDE website. 

Now I want to install KDE. Just want to know whether can do it with dpkg. Is any Hoary specific tweaking required to be done?

Thanks.

Raj

---

### Post by getaceres on 2005-09-09
You are going to have a lot of unresolved dependencies. Try this:
Download kubuntu ISO and burn it to a CD.
Add the cdrom as a source to apt (look for apt-cdrom command).
Then do:
apt-get install kubuntu-desktop

Once it's installed, try to install through dpkg the packages from KDE 3.4.2 that you have downloaded. It should give you a lot less unresolved dependencies if any at all.

---

### Post by byen on 2005-09-09
why not just apt-get directly from the repositories?

---

### Post by Kyral on 2005-09-09
[b] I don't have internet connection where in my linux box.

[/b]Maybe thats why? ;-)

---

### Post by aysiu on 2005-09-09
[QUOTE=byen]why not just apt-get directly from the repositories?[/QUOTE] No internet connection from the Linux box. It's in the first post.

---

### Post by byen on 2005-09-09
[QUOTE=aysiu]No internet connection from the Linux box. It's in the first post.[/QUOTE]
 lol...sorry.. gotta "focus" a lil more next time ;-) PS2 is ruining my life...

---

### Post by rajsarkar on 2005-09-13
Thanks for all the responses. 

I tried to install all the KDE .tar.bz2 files. But none of the files could configure. Error message was like this - "important file KDE.config  missing"

I think this "KDE.config" is related to ubuntu installation. If I could make .deb files then I could have used "dpkg" to install the files. But transforming the .tar.bz2 files into .deb package seems to be cumbersome and complex. Perhaps not suitable for a newbie like me. 

Another way could be to use KConstruct to make the .deb package. 

If there is anyother simpler method pls let me know.

Thanks and  regards,

Raj

---

### Post by getaceres on 2005-09-13
[QUOTE=rajsarkar]Thanks for all the responses. 

I tried to install all the KDE .tar.bz2 files. But none of the files could configure. Error message was like this - "important file KDE.config  missing"

I think this "KDE.config" is related to ubuntu installation. If I could make .deb files then I could have used "dpkg" to install the files. But transforming the .tar.bz2 files into .deb package seems to be cumbersome and complex. Perhaps not suitable for a newbie like me. 

Another way could be to use KConstruct to make the .deb package. 

If there is anyother simpler method pls let me know.

Thanks and  regards,

Raj[/QUOTE]

I don't know. I've never built KDE from sources but konstruct is the right way to do it.
What's the problem of adding the kubuntu CD as a repository and then installing KDE 3.4.2 from the kubuntu site?

---

### Post by rajsarkar on 2005-09-14
I think you missed the first post. I don't have internet connection where my Linux box is nor do I have Kubuntu CD. Probably I'll get a Kubuntu CD next week. However I am planning to go ahead with KDE installation from source. I downloaded all other required sw like Konstruct, automake and autoconf. For the sake of doing R&D. 

Shall post the outcome later.

Thanks.

Raj

---

### Post by getaceres on 2005-09-14
[QUOTE=rajsarkar]I think you missed the first post. I don't have internet connection where my Linux box is nor do I have Kubuntu CD. Probably I'll get a Kubuntu CD next week. However I am planning to go ahead with KDE installation from source. I downloaded all other required sw like Konstruct, automake and autoconf. For the sake of doing R&D. 

Shall post the outcome later.

Thanks.

Raj[/QUOTE]
 If you want to build it from sources, then go ahead. I'm not stopping you.
What I said is that:
1. You download the Kubuntu ISO in a PC with internet connection (the same you used to download the KDE source packages). Then you burn it to a CD.
2. You download the KDE 3.4.2 packages from the kubuntu site and burn them to another CD (or USB stick or whatever other media).
3. Now offline, in your Ubuntu system, you add the Kubuntu CD you have downloaded in step 1.
4. Install KDE 3.4 from synaptic. It should not have unmet dependencies because all of them are in the Kubuntu CD that you have.
5. You install KDE 3.4.2 from the media you have it in step 2 by dpkg -i *.*. It should give you some unmet dependencies, but they are not more than the sources might ask you. 
6. Go to the PC with Internet and download the remaining packages and then, offline, install it in the Ubuntu box.

Anyway, compiling and installing from sources might not be bad, but the Kubuntu packages are tested to work well with a Ubuntu system. The sources might give you problems.

---

