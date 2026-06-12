---
title: "Writing chinese characters"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2007-11-04
Hi
My girlfriend is chinese, i am trying to bring her over to Linux, (any way to get qq and qq zone, which is only usable in internet explorer working?) Anyway, i've been trying to get Ubuntu to let her write Chinese, i tried following this advice
[http://ubuntuforums.org/showthread.php?p=3668857](http://ubuntuforums.org/showthread.php?p=3668857)
but i don't get the system -> preferences-> global setup option, what can i do?

And, how do i make shortcuts to places or applications in Ubuntu?

---

### Post by nab on 2007-11-04
Hi,

As far as I know there is a chinese distribution based on Ubuntu: dubuntu
You can find some remarks on the chinese ubuntu forum, e.g. [http://forum.ubuntu.org.cn/forum-79.html](http://forum.ubuntu.org.cn/forum-79.html)

Hope this helps,
Niko

---

### Post by Falc7 on 2007-11-04
thanks for the reply
I would rather not have a complete chinese distribution though,** I** still need to use the computer :)
Just want to let her write chinese in her chinese sites

---

### Post by rudeboyskunk on 2007-11-04
You could always try making the computer dual-boot, have her partition for dubuntu and yours ubuntu.

---

### Post by nrfool on 2007-11-04
can you search "global setup option" with ubuntu? In addition, maybe check the menu editor to make sure "global setup option" is selected.
As for QQ and QQ zone, the best way is probably just use virtualbox and have a copy of windows there. QQ is one evil piece of software that constantly changes itself to break any 3rd party application.

---

### Post by Falc7 on 2007-11-04
thanks for the QQ tips, out of curiosity, why would the developers of QQ want to break any 3rd party application?

I tried searching for global options, but it gave me results like evolution 2.12 User guide, and some reference manual, nothing useful.

Where is the menu editor? i tried searching for it in the help box but it couldn't help me

---

### Post by nrfool on 2007-11-05
I have a suspision that "global options" mentioned in the reference post is referring to the global options in SCIM, rather than ubuntu. The following is how I added Chinese input in xubuntu gusty, I hope it works for you too.
System->language support->select "Chinese", apply
Step 2:
Then go to SCIM input method setup, IMEngine->Chinese (traditional/simplified/or both)->choose the input method.
Hit apply.
I don't remember exactly, but I think you will need to restart ubuntu either after step 1 or step 2.

As for QQ. Basic QQ functions are free for users. The company mostly makes it's money by serving ads and providing charged "premium" services. As a result, it is to the company's benefit to make the official version of QQ the only working version. Because 3rd applications (such as pidgin) will essentially deprive the company's ability make money from ads.

---

### Post by Falc7 on 2007-11-05
cheers
I feel we are getting closer to solving this
I've found the SCIM input method setup menu.
There seem to be a list of lots of languages under IMEngine -> global setup. All of them are enabled, including chinese simplified. There are several different sub options under the header chinese simplified as well, all of these are selected.

But still no way to write chinese, i looked under font end global setup, it says the trigger to switch to the language (i have no idea how it knows which language to switch to) is control and space, but it has no effect.

---

### Post by Falc7 on 2007-11-05
I still can't seem to get that little button to change into pinyin to character conversion. :-(

---

### Post by changcheng on 2007-11-05
I´ve got the same problem with yours, I am still working on it. It seems changing the default language to Chinese and Login again can help. But it will make the system fonts in mass.

---

### Post by changcheng on 2007-11-05
Here, I found it on other post, this solved my problem. You must install a scim-bridge to solve the problem.

sudo apt-get install scim-bridge
sudo gedit /etc/X11/xinit/xinput.d/scim

then find and change

GTK_IM_MODULE=xim

into

GTK_IM_MODULE="scim-bridge"

Restart system. SCIM should works fine with all applications. Maybe you will need start SCIM manually by


SCIM -d

---

### Post by Falc7 on 2007-11-06
I love you

---

### Post by cibby on 2007-12-30
I know this is an old thread, but to comment on the QQ issue: I've successfully used Pidgin to let my girlfriend chat on QQ. It's not fault-free, though, but it's workable...

---

### Post by countrylaketj on 2008-01-02
> **changcheng said:**
> Here, I found it on other post, this solved my problem. You must install a scim-bridge to solve the problem.

sudo apt-get install scim-bridge
sudo gedit /etc/X11/xinit/xinput.d/scim

then find and change

GTK_IM_MODULE=xim

into

GTK_IM_MODULE="scim-bridge"

Restart system. SCIM should works fine with all applications. Maybe you will need start SCIM manually by


SCIM -d

Hi, I have a different problem. In my System --> Administration --> Language Support there is only English. When I ran

sudo apt-get install scim-bridge

I got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package scim-bridge is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package scim-bridge has no installation candidate

What's wrong? I installed ubuntu 7.10 from downloaded CD with English as default language. It seems support for other languages were not installed but I don't know how to add them.

---

### Post by sammysun on 2008-01-02
> **cibby said:**
> I know this is an old thread, but to comment on the QQ issue: I've successfully used Pidgin to let my girlfriend chat on QQ. It's not fault-free, though, but it's workable...

You can install eva for QQ.:)
sudo apt-get install eva

---

### Post by Yumi on 2008-01-02
For QQ you can use lumaqq . It works for messages, I do not know if video and speech is suported.

Michael

---

### Post by Tech_Power888 on 2008-01-21
> **sammysun said:**
> You can install eva for QQ.:)
sudo apt-get install eva


Hey,my qq seems dosent work very well at all&#12290;It kept disconnecting itself, and didnt let me to add freinds. 

I tried to instal eva. but nothing seemed changed...any idea?

Thanks.

---

### Post by khughitt on 2008-01-22
Pidgin now supports QQ I believe, but you also try "eva" for chat.

---

### Post by cablop on 2008-02-22
Yes LumaQQ is a nice piece of software, but it have it downsides, does not support all the features of a real QQ, and all the documentation is in chinese (but having a chinese girlfriend...).

Pidgin also lack on features, but is more easy to integrate with your desktop environment, of course it is GTK so i expect it to work well with SCIM. I wonder about the encodig in QQ, cause in windows it seems to be big5 or gb...

There's a lot of guides to easy integrate SCIM for chinese writing in ubuntu, and all of them have their downsides. In my experience the best working configuration is Feisty + SCIM. Edgy has one problem, you make it work or not. If you failed installing it on Edgy, you must reinstall al or start doing a hard debugging. Gutsy works perfect (with a little fix) but only for GTK, KDE needs tricky settings, and other software not GTK nor QT is not allowed, for example... aMSN (the weird thing is, i made it work with aMSN just one time, but it does not wotrk with KDE...).

DO you need help? you can pm or contact me by messenger and i'll try to help about that issue on weekends.

(If i could develop something for linux, i'll rewrite SCIM from scratch... hehe if somebody paid me for such development i'll be glad do to that)

---

### Post by Falc7 on 2008-02-23
From what i've seen eva dosen't support writing chinese characters, pidgin does, but pidgin can't do some other stuff, its what i use now

---

### Post by Kosimo on 2008-02-23
Multilingual Keyboard support in Ubuntu is a mass!!  I hate it...
I tried installing korean keyboard support for hangeoul letters, I used SCIM adding support bla bla bla...

Then my keyboard behavior was completly wired... Someties I couldn't write when renaming files in nautilus, pidgin stop writing then I couldn't change from hangeoul to catalan language as I use to have..  Bahh... I've never got this working. 

One of my dreams in this area is having a Catalan keyboard, and switch to korean alphabet easily without compromising my system.. Do I'm asking too much?   Why is THAT COMPLICATED?!?!

Ubuntu devs... Please, create some easy GUI to switch keyboards with a simple click..


PLEASE!!!

---

