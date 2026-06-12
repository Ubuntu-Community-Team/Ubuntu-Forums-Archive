---
title: "Newbie question: .deb binaries and building from source"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by 5parrowhawk on 2005-11-13
Hi, I just got Ubuntu 5.10 up and running with a net connection. (Nearly 5 hours of troubleshooting... bleah.) I've been trying to install xmms, but ran into some trouble.

1. When attempting to compile from source, it tells me that g++ isn't configured correctly. Is there some config file I need to edit, or am I missing some packages? (When usijng Synaptic I had noticed earlier that g++ and some other packages, including the linker, were missing, so I had installed them at that point. Other than that my installation is pretty much stock.)

2. After failing to compile, I went looking for a binary distribution. I found one for Debian, but can't figure out how to install it. Do I just extract everything to the appropriate directories (with superuser privileges), or will that break stuff?

3. And I notice that there's an xmms patch from one of the Ubuntu developers(?). How does one install the patch?

Thanks in advance!

---

### Post by davmac on 2005-11-13
1. If you install "build-essential" it'll make sure you've got everything you need for compiling from source.

2. If you've downloaded the .deb file, you can install it by opening a terminal and typing "sudo dpkg -i thefilename.deb"

3. Don't know this one...

Regards,

Dave Mac

---

### Post by Mustard on 2005-11-13
Is there some problem with the xmms available through the ubuntu repositories?

---

### Post by emperor on 2005-11-13
[quote=Mustard]Is there some problem with the xmms available through the ubuntu repositories?[/quote]

XMMS should be in the std repos but most of the add-ons are in the "universe". 

You can enable "universe" and "multiverse" repos in /etc/apt/sources.list".

---

### Post by 5parrowhawk on 2005-11-13
Thanks for all the help. I didn't realise the repository was that extensive!

---

### Post by az on 2005-11-13
13000+ packages, I think.

Yes, 13k.

And every single on has a debian maintainter to make it, and Ubuntu has a team of packaging ninjas (MOTU - Masters of the universe) to make sure they run and integrate well with Ubuntu.

---

### Post by kelsey23 on 2005-11-13
I don't understand why you are compiling from souce. Ubuntu GNU/Linux comes with XMMS by default, and there already is a binary in the repostories if for some reason you don't have it installed right away. Also, all I had to do to install g++ on my system was:

sudo apt-get install g++

I installed all of the recommended packages, too I belive.

---

### Post by emperor on 2005-11-13
[quote=azz]13000+ packages, I think.
[/quote]

17,767 when universe and multiverse are enabled!

---

