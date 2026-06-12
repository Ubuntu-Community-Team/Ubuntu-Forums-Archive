---
title: "A few &quot;What Not to Dos&quot;....Definitely a Learning Process"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Nameless on 2005-12-22
Well, I finally got my computer back up and running again and I thought I'd post a "How Not To" do some things for those of you that might be as much of a noob as I am. 

First off, I found a ton of great a help in this forum, so I wanted to say Thanks! to those that read the posts and offer help to those of us in the in the Beginner's Forum.  It's really helpful for people like me.  

On to some what not to dos: 

1) Do not play around with the xorg file unless you really have a great grasp on what the heck you're doing.  While trying to change my monitor resolution, I managed to get my system stuck and all I could see was a giant terminal window taking up the entire screen. I didn't really know what to do there, (I would love to know what I should have done here!!) so (in a windows mentality) I just rebootted >>>>

2) Do not just reboot when all you have is a terminal screen.  Not knowing the commands really killed me here, because when I rebooted I was able to get to the Gnome/login screen, but as soon as I enter my password, Gnome crashed and my monitor turned off.  All I could do was reboot and start the cycle over again.  Not as much fun as I had hoped it would be.

My solution to this problem was to just boot windows and use partion magic to remove the Ubuntu partition and reinstall >>>>>

3) Do not just delete a the Ubuntu partion.  What I didn't consider was that the MBR was on the windows partion and would require the Ubuntu info to work.  I wasn't able  to boot into anything.  CRAP! This was by far the highlight of noob-ness for me.  

For those that might try this the only way to fix this is to either: 1) Get your original Windows disc and do a recovery of the MBR (Guess what disc I couldn't find???) or 2) Reinstall Ubuntu!

Since I wasn't ready to give up on Linux (dammit I'm going to learn this one way or another) I was able to start the installation process a new.  Luckily this actually worked and I was able to increase the Linux partition (b/c I really am commited to making this work). 

So after a couple of nights of utter frustration, I'm back to where I started and this time I ordered a couple books so that I could get a good basis for Linux before I get carried away. 

Maybe this will help a couple people, or maybe I'm the only one that's doing things quite this poorly.  Either way, I wanted say Thanks! again to those that help the noobs here.  I scoured the forums and was able to find almost all the answer I needed...Thank you! your help is appreciate.

---

### Post by Pablo_Escobar on 2005-12-22
Everyone was a nOOb at the beginning.
It's important to learn from the mistakes You make, and learn as much as You can.

I can remember myself trying out the first distro - Aurox (a couple of years back) with no net connection.
I was eager to compile something so I downloaded some app source from a friend of mine who had a net connection, copied to my box. Then I unpacked it, typed ./configure in great anticipation for a wonderfull and long compilation process. After a split second the terminal borked missing for some dev package. I was so mad at the distro that it's broken and it wouldn't let me compile stuff (I should've read and learn more :D ) so I erased the partition and made a new one for my Win. - terrible times :P

So, keep Your head up and don't discourage Yourself :)

---

### Post by Nameless on 2005-12-22
[QUOTE=Pablo_Escobar]
So, keep Your head up and don't discourage Yourself :)[/QUOTE]

Yeah, it was discouraging for the first two nights, but I think once I've made the mistakes, that's the best part, b/c I guarantee you I will never delete the partition again.  :) 

All in all, I'm growing to like the flexibility and on my second install the resolution was the way I wanted to be before I started fooling around with it.  Strange how that happens.  

These forums have a wealth of info....If only I could read them all quickly.

---

### Post by Rinzwind on 2005-12-22
> **Nameless]Well, I finally got my computer back up and running again and I thought I'd post a "How Not To" do some things for those of you that might be as much of a noob as I am. 

First off, I found a ton of great a help in this forum, so I wanted to say Thanks! to those that read the posts and offer help to those of us in the in the Beginner's Forum.  It's really helpful for people like me.  

On to some what not to dos: 

1) Do not play around with the xorg file unless you really have a great grasp on what the heck you're doing.  While trying to change my monitor resolution, I managed to get my system stuck and all I could see was a giant terminal window taking up the entire screen. I didn't really know what to do there, (I would love to know what I should have done here!!) so (in a windows mentality) I just rebootted >>>>[/QUOTE]
I'm just as a newbie as you BUT. You knew what your changed didn't you? 
Under CLI (command line interface  said:**
> 

2) Do not just reboot when all you have is a terminal screen.  Not knowing the commands really killed me here, because when I rebooted I was able to get to the Gnome/login screen, but as soon as I enter my password, Gnome crashed and my monitor turned off.  All I could do was reboot and start the cycle over again.  Not as much fun as I had hoped it would be.
I did that too the 1st time. With a faulty splash screen :D
> 
My solution to this problem was to just boot windows and use partion magic to remove the Ubuntu partition and reinstall >>>>>

Been there. Done it too :)
Just 1 thing after you deleted it do a
c:fixmbr 
from a dosbox ;)
> 
3) Do not just delete a the Ubuntu partion.  What I didn't consider was that the MBR was on the windows partion and would require the Ubuntu info to work.  I wasn't able  to boot into anything.  CRAP! This was by far the highlight of noob-ness for me.  

For those that might try this the only way to fix this is to either: 1) Get your original Windows disc and do a recovery of the MBR (Guess what disc I couldn't find???) or 2) Reinstall Ubuntu!
I did that too once :D 
> 
<..>
Maybe this will help a couple people, or maybe I'm the only one that's doing things quite this poorly.  Either way, I wanted say Thanks! again to those that help the noobs here.  I scoured the forums and was able to find almost all the answer I needed...Thank you! your help is appreciate.

You tried. 
You failed. 
You started over. 
You learned (I hope ;) ).

Hey we all went the same way. Even the best of the best where it comes to Ubuntu/Linux have seriously f***ed up their system.

---

### Post by bscbrit on 2005-12-22
[QUOTE=Nameless]
Since I wasn't ready to give up on Linux (dammit I'm going to learn this one way or another).... .[/QUOTE]

That's the best part of all of this - rather than be defeated, you are determined.! If only more people didn't give up at the first hurdle.

---

### Post by Nameless on 2005-12-22
[QUOTE=Rinzwind]
Been there. Done it too :)
Just 1 thing after you deleted it do a
c:fixmbr 
from a dosbox ;)

[/QUOTE]

The only problem with the C:fixmbr was that Partition Magic automatically rebooted the computer after I deleted the partition and the system automatically tried to find GRUB so I wasn't even able to get to the c:prompt.  UGH!  Lesson learned :)

---

### Post by futz on 2005-12-22
> Under CLI (command line interface  ) 'vi' is your GOD. vi /etc/xorg
Man, I wouldn't recommend vi to anyone, especially beginners. It's so totally confusing. Use nano instead. It's pretty simple to understand, even for a newb.

---

### Post by Rinzwind on 2005-12-22
> **Nameless]The only problem with the C:fixmbr was that Partition Magic automatically rebooted the computer after I deleted the partition and the system automatically tried to find GRUB so I wasn't even able to get to the c:prompt.  UGH!  Lesson learned :)[/QUOTE]

LOL. That's true. Damn :( 
Ok NEXT time. 1st do the fixmbr and then the deleting  said:**
> Man, I wouldn't recommend vi to anyone, especially beginners. It's so totally confusing. Use nano instead. It's pretty simple to understand, even for a newb.

Hmmm sorry I'm more of a Unix man when it comes to editting from the prompt and all I got is vi :( But yes, nano is very cool!

---

### Post by JasonL on 2005-12-22
Its kind of freaky that your mistakes are almost identical to mine. I don't currently have Ubuntu installed but i am determined to not let any problem get in my way, glad to hear you share the same determination.

Also seeing as this is my first post, hi to the great community that we have here, you already cannot imagine how useful and helpful you have been to me :D .

JasonL

---

### Post by Nameless on 2005-12-22
[QUOTE=futz]Man, I wouldn't recommend vi to anyone, especially beginners. It's so totally confusing. Use nano instead. It's pretty simple to understand, even for a newb.[/QUOTE]

Ok, I wasn't going ask about this until I got home and had a little more time to research this: It sounds like I should shy away from "vi", but what is "nano"?

---

### Post by futz on 2005-12-22
[QUOTE=Nameless]Ok, I wasn't going ask about this until I got home and had a little more time to research this: It sounds like I should shy away from "vi", but what is "nano"?[/QUOTE]

They're both tiny text editors for the command line terminal. 

Vi is old and wierd and extremely alien to anybody who didn't start computing in the 70's. It only shows one line at a time or something like that. I only tried it once and ran screaming to nano. Real klunky.

EDIT: I just remembered that I used to use vi in the early 80's on my trs-80 color computer system with the OS-9 operating system (basically unix). Didn't take me long to switch to emacs, cuz vi was terrible.

Nano is still a bit old fashioned, but pretty easy to figure out, as it has a menu at the bottom to help you. And it displays a page of text at a time, so you can make sense of what you're editing, by having some context.

---

### Post by wombat20 on 2005-12-22
Hands up here too.  I've made plenty of those mistakes.

That's why it's best to have a friend to help you along the first time.  Otherwise it can be quite scary.  For those who've learnt important lessons the thing is to pass on that experience to friends or family.  So even if you're not a programmer you can contribute to this community thing.  Humans are programmed to be altruistic - if you're not kind to somebody at least, then something has gone wrong.

The ideal people to help out are those with basic needs (email, web, office apps).  Those who have little windows knowledge (so less to unlearn).  Those who are looking at getting a new/first computer (no dual boot stresses).  Anyone concerned with security will benefit from Linux.

---

### Post by JasonL on 2005-12-22
I like the idea of the Linux communities and helping each other, a lot better than any Microsoft support you can get. I have already started passing Ubuntu on and my friend tried it with the live CD, he wants to do a dual boot with XP and I am going to help him get it running. I figure if the both of us start using Linux together we can help each other along the way, learn from each others wrong doings and also two people searching on how to do something is better than one.

---

### Post by futz on 2005-12-22
[QUOTE=JasonL]I like the idea of the Linux communities and helping each other, a lot better than any Microsoft support you can get. I have already started passing Ubuntu on and my friend tried it with the live CD, he wants to do a dual boot with XP and I am going to help him get it running. I figure if the both of us start using Linux together we can help each other along the way, learn from each others wrong doings and also two people searching on how to do something is better than one.[/QUOTE]
Having a second machine right there, connected to the interweb is a HUGE help too. Cuz if you've borked the first machine and need to dig for online help to fix it, you'll need it.

---

### Post by JasonL on 2005-12-22
True, re mind's me of when I got all the information I needed for Ubuntu saved in my bookmarks on XP, then went into Ubuntu to start learning and got stuck, needed the website addresses and couldn't get them. Luckily my sister lent me her laptop and I got the information from that, definitely helps to have another source of internet access when you have just come into Ubuntu or Linux.

---

### Post by Nameless on 2005-12-22
[QUOTE=futz]Having a second machine right there, connected to the interweb is a HUGE help too. Cuz if you've borked the first machine and need to dig for online help to fix it, you'll need it.[/QUOTE]

This is what saved me from throwing my machine out the window.  I had my laptop (zv6000 - so its not going to Ubuntu anytime soon) right next to it to figure out what I needed to do. 

[QUOTE=futz]Nano is still a bit old fashioned, but pretty easy to figure out, as it has a menu at the bottom to help you. And it displays a page of text at a time, so you can make sense of what you're editing, by having some context.[/QUOTE]

How do I get this? or do I have it already?  I would love to find anything that will help me with terminal.

---

### Post by futz on 2005-12-22
[QUOTE=Nameless]How do I get this? or do I have it already?  I would love to find anything that will help me with terminal.[/QUOTE]
It's installed by default in Ubuntu and many other distros. Just type "nano yourfiletoedit" (without the quotes). 

In nano, the ^X type commands in the menu mean CTRL-X and so on.

If you're in another distro and it doesn't have nano, try pico. Very similar (a fork from nano? or vice-versa?).

---

### Post by estel on 2005-12-22
Nano describes itself as an "Enhanced Free Pico Clone" So I imagine the latter :)

---

### Post by matthew on 2005-12-22
As vi vs nano vs emacs can get into an argument akin to a religious war

and

as this is offtopic anyway

I propose we get back on topic...here we go

We have all been newbies and we have all made frustrating errors. I made one that required a complete reinstall about 3 days after my first Linux installation. I figure that since I was the only person going to be using my computer that the whole file permissions thing was unnecessary...big mistake. I typed
```
sudo chmod -R 777 /
```which reset the file permissions on my entire hard drive...and made program after program not work. Upon a reboot attempt the reboot failed. Not knowing what to do or how to sort out all the permissions and get them set back where they needed to be I just reinstalled.

The other one that I have never made, but that I have heard of was to type```
sudo rm -R /
```

Two primo examples of "What ***NOT ***to do."

---

### Post by estel on 2005-12-22
That latter one I did on DOS once upon a time. Being a naive youngster, I was looking for a way to clear up a bit of Diskspace for Lemmings or something, and looking for some erroneous folder / files.

In C:\Program Files I found this folder called ".." and thought "I don't think that I need that :)"
```
deltree ..
```

---

