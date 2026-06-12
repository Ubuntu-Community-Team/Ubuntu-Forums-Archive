---
title: "Java and firefox. GOt the download. Now what ?"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by weasel fierce on 2005-06-21
I regular play roleplaying games (D&D stuff) on java based digichats, so I am trying to make java work under firefox.

So far, I have downloaded the file jre-1_5_0_02-linux-i586.bin file, which I found from the java website. However, the online directions I have found to make it work havent seemed to do much good.

Any kind people who could assist ?

---

### Post by poofyhairguy on 2005-06-21
[QUOTE=weasel fierce]I regular play roleplaying games (D&D stuff) on java based digichats, so I am trying to make java work under firefox.

So far, I have downloaded the file jre-1_5_0_02-linux-i586.bin file, which I found from the java website. However, the online directions I have found to make it work havent seemed to do much good.

Any kind people who could assist ?[/QUOTE]


Lets not do it that way mate.

That way takes like ten commands I don't understand to work.

Lets do it this way:

First do what this step says, exactly!

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Then enter this command into the terminal:

> sudo apt-get install sun-j2re1.5

---

### Post by weasel fierce on 2005-06-22
You sir, are my hero :)

Did what you suggested, and its working swimmingly

---

### Post by Ray Hamilton on 2005-06-22
Sorry, but I tried this and get the following:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

How come it doesn't work for me? (Originally the lines in sources.list referred to gb. rather than us. but I have tried it with both and get the same.

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=Ray Hamilton]Sorry, but I tried this and get the following:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

How come it doesn't work for me?[/QUOTE]

You sources.list doesn't have the backports added. Make sure to copy the last two lines:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then enter this command:

> sudo apt-get update

And try to install Java again.

---

### Post by aleahey on 2005-06-22
[QUOTE=poofyhairguy]You sources.list doesn't have the backports added. Make sure to copy the last two lines:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then enter this command:



And try to install Java again.[/QUOTE]

i did it this way and it still doesnt work within firefox, (im using 1.0.4), what the _hell_?

---

### Post by desdinova on 2005-06-22
Did you install FF via the repositories as well?

---

### Post by aleahey on 2005-06-22
[QUOTE=desdinova]Did you install FF via the repositories as well?[/QUOTE]


hm, no sir i did not. i used the package from the mozilla website. should i do apt-get remove and reinstall?

---

### Post by desdinova on 2005-06-22
Yep - as the java deb knows where to find the ff deb as they're linked - whenever you can, it is always best practice to use deb's

---

### Post by Kapre on 2005-06-22
Poofy - I'm still a noobie (please bear with me) Can I install this via the synaptic (cause I see it in the synaptic window)?

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=Kapre]Poofy - I'm still a noobie (please bear with me) Can I install this via the synaptic (cause I see it in the synaptic window)?[/QUOTE]

Oh yeah....Synaptic is nothing but a pretty wrapping for apt-get. One can do everything the other can do.

The only thing that matters is that you have the correct repositories enabled like the first part of the ubuntu guide says:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

You can do that in synaptic too...but it takes a lot longer and has room for error.

Then be sure to click the update button in synaptic. I love synaptic too. I tell people commands here (and it is done this way on the guide) because there is less room for error. No one can mess up copy and paste.

If you need more help, ask anything.

---

### Post by Kapre on 2005-06-22
Poofy - thank you very much. That is why I like Ubuntu than any other distro because of the support of this community (forum).

Thanks again and more power.

K

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=Kapre]Poofy - thank you very much. That is why I like Ubuntu than any other distro because of the support of this community (forum).

Thanks again and more power.

K[/QUOTE]

No problem.

---

### Post by aleahey on 2005-06-22
hm. still no go on the java :\

---

### Post by buchan on 2005-06-23
aleahey, just out of curiosiy... what kind of system do you have? 

I have an AMD 64 and so I am running a 64bit system and I'm having the same issues as you.  Could this be an AMD 64 problem IE there is no version of 64 bit java in the repositories??

---

### Post by Ray Hamilton on 2005-06-23
Thanks poofyhairguy.  Entered the last two lines as suggested, guess my eyes were half closed the first time and I missed typing them.  Everything works as it should - tested it out at java.com.

You're the man.

Ray

---

### Post by Kvark on 2005-06-23
edit: ignore me, there was a lot less posts here when I started typing this reply, gotta stop going away doing other things and then come back to hit post button later, after others already said it.

---

### Post by tszanon on 2005-06-23
[QUOTE=buchan]aleahey, just out of curiosiy... what kind of system do you have? 

I have an AMD 64 and so I am running a 64bit system and I'm having the same issues as you.  Could this be an AMD 64 problem IE there is no version of 64 bit java in the repositories??[/QUOTE]
I believe this problem is related to AMD64, because I read on java.sun.com that support for 64 bits has been added in the jdk1.5 update 2, BUT the 64 bit plugin isn't available yet.

Maybe we can solve this problem installing the 32 bit jre manually. I haven't tried it yet, but if it works, it may be a workaround until Sun finally releases a 64 bit java plugin.

If I'm right, it explains why we just don't find the sun-j2re1.5 package in the repositories: there is a 32bit version, but no 64bit version (with a plugin) available.

Gotta keep trying.

Edit: just remembered to say that I'm using the Firefox that was installed during OS installation. I even downloaded a "new" version from Mozilla site and tried to install it, but (guess what?) I couldn't make it work. hehehe  8-[

---

### Post by Dave_is_sexy on 2005-06-23
Hmm. My java works fine (Azureus etc), but not as a firefox plugin. Which is weird. Firefox is the one which came with ubuntu (1.02)

---

### Post by Kapre on 2005-06-23
Got it working on Ephipany, Mozilla and Firefox....Thanks again poofy....

aleahay - did you try using the other browsers?

K

---

### Post by buchan on 2005-06-24
Well, I can confirm that the problems I was running into were because of the version I was running.  

I have now loaded the X86 version and followed all of the instructions ... everything worked perfectly.

I was running Fedora before this and it was the same way, there were a lot of AMD64 packages missing compaired to the X86 version. 

If you're looking for an everyday version of Unbuntu even on an AMD 64 you're probably better off sticking with the X86 version.

---

### Post by tszanon on 2005-06-24
[QUOTE=buchan]If you're looking for an everyday version of Unbuntu even on an AMD 64 you're probably better off sticking with the X86 version.[/QUOTE]
Suppose I install the x86 version. Is there an easy way of "upgrading" to the AMD64 version? When i say "an easy way" I mean anything but a complete system reinstall.

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=tszanon]Suppose I install the x86 version. Is there an easy way of "upgrading" to the AMD64 version? When i say "an easy way" I mean anything but a complete system reinstall.[/QUOTE]


Not really. Even though it seems like it to us....one is not the upgrade of the other. The programs are the same version...the 64 bit version is just packaged differently.

As a general rule there is nothing easy about the 64 bit version. You know these problems you have with the 64 bit version? there is only one way to fix that:

[http://www.ubuntuforums.org/showthread.php?t=24575](http://www.ubuntuforums.org/showthread.php?t=24575)

And that one way will still be the same after Breezy. If you want that version...just role up your sleeves and do this now because it won't get better for some time.

---

### Post by tszanon on 2005-06-24
I read it and all I can say is: it seems to be a very good workaround for the problem. Since there is no answer for the question "when will package ___ be available for AMD64?", that's what I shall do next.

I think my post is going a little off-topic, but I'm gonna ask anyway: after this AMD64 problem is finally solved, would it be difficult to undo the chroot thing? Would it be just uninstalling it through Synaptic, removing the remaining directories in /chroot (if any), and installing the AMD64 version of the desired packages? :-?  :confused:

---

