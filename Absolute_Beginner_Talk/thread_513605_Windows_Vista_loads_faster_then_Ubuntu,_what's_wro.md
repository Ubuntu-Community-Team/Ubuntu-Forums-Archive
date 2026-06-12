---
title: "Windows Vista loads faster then Ubuntu, what's wrong ?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by pikul on 2007-07-30
My new desktop came with Windows Vista, it has a lot of software already installed and i added some more, it works great, but i don't like it :lolflag: on the second week off using it i pop my Ubuntu Feisty cd and install it, everything worked out of the box,  and i been using it since then, works great and it looks amazing with Compiz, with that said.

i don't understand why Vista loads faster then ubuntu, the overall performance its good, and i can get a login screen on exactly 23 seconds, and didn't mod anything :confused: i did a lot of mods on Ubuntu but still can get it to load faster, my bootchart saids that it loads on 20 secs. but i don't get a login screen until the 38 sec. i have use the same clock to check times on both loadings, i think the problem its with GDM :( i remove the the splash screen to see whats going on, and everything its ok.

I know they are totally different but everybody saids that vista sucks and its not what i've been seeing :mad: as i said before, the overall performance its good, this doesn't mean im going to start using vista on daily bases, but it's kind off sad lol just my 2 cents jajaja 

Can someone help to speed up my boot times ? as i said, i think there's something wrong with GDM :(

Specs: Intel Core 2 Duo @ 1.8 ghz 1 gig of ram 256 integrated Video 

My Bootchart:

[img]http://img130.imageshack.us/img130/5/20seg1lo3.png[/img]

Thanks  :guitar:

---

### Post by Patrick-Ruff on 2007-07-30
wow, I'm sure someone will assist you, I however can't but I'd just thought I'd marvel on your detailed information here.  really respectable, good job.

---

### Post by p_quarles on 2007-07-30
I dual-boot Vista and Ubuntu as well, and I've found that while I get to the desktop faster in Vista, it continues to load a bunch of startup programs for the next two minutes or so (anti-virus, update manager, "firewall", account settings, etc). When Gnome shows up, on the other hand, it's ready to go.

---

### Post by Jellicletrb on 2007-07-30
I'm terribly ashamed to admit that I haven't "Vista'd" at all yet  :(

---

### Post by Sayers on 2007-07-30
KDE boots fast ;P , yes On XP my mom's computer takes forever to boot and forever for the desktop to start everything

---

### Post by Sayers on 2007-07-30
> **Jellicletrb said:**
> I'm terribly ashamed to admit that I haven't "Vista'd" at all yet  :(

Ashamed!?

---

### Post by p_quarles on 2007-07-30
> **Jellicletrb said:**
> I'm terribly ashamed to admit that I haven't "Vista'd" at all yet  :(
You're not missing anything.

---

### Post by Jellicletrb on 2007-07-30
> **Sayers said:**
> Ashamed!?

Well, I like to appear opened minded  :)

---

### Post by Sayers on 2007-07-30
being rude and stubbern is fun

---

### Post by Patrick-Ruff on 2007-07-30
uh, you guys DO know that someone needs HELP here?  right?  stop the nonsense and help him.

---

### Post by shae on 2007-07-30
Ubuntu simply loads slower than vista.  There are several reasons for this.  Vista is made as a desktop operating system while linux's roots are on servers, where boot up speed is not a priority.  However, linux is meant to have long uptimes.  Try out a windows install that hasnt rebooted in 10 days and try out a linux one.  Windows will be crawling while Linux is as fast as when it was booted.

Now certainly there are means by which you can speed up the boot process.  One of these is to disable anything that is loaded at startup that is not used.  Examples of this are things such as bluetooth and HP printer drivers.  These will not dramatically increase your boot up time though.  It is really not worth it.  What is 10 seconds?  Surely you do not have to boot up that often.

---

### Post by shen-an-doah on 2007-07-30
> **p_quarles said:**
> I dual-boot Vista and Ubuntu as well, and I've found that while I get to the desktop faster in Vista, it continues to load a bunch of startup programs for the next two minutes or so (anti-virus, update manager, "firewall", account settings, etc). When Gnome shows up, on the other hand, it's ready to go.

That's the thing with Windows vs Ubuntu/Linux. Windows loads various things after you've logged in, whereas Ubuntu loads anything vital before GDM comes up so you're ready to go as soon as you've logged in (with the exception of any startup programmes you might have set yourself).

Try timing how long it takes for you to boot up, log in and start something simple like Firefox and then compare the times...

---

### Post by p_quarles on 2007-07-30
Well put, shae. The only thing I would add is this: when a program crashes your desktop, it's a *lot* faster to reload the GUI than it is to reboot the entire system.

---

### Post by pikul on 2007-07-30
> **Patrick-Ruff said:**
> uh, you guys DO know that someone needs HELP here?  right?  stop the nonsense and help him.

:lolflag:

I know vista starts loading stuff after i login with my user but its not slow even then, as i said, i have a lot of software install on vista by default :lolflag: :confused: its pretty much like ubuntu needing to load compiz, Gdesklets and other stuff :popcorn:

---

### Post by pikul on 2007-07-30
> **shae said:**
> Ubuntu simply loads slower than vista.  There are several reasons for this.  Vista is made as a desktop operating system while linux's roots are on servers, where boot up speed is not a priority.  However, linux is meant to have long uptimes.  Try out a windows install that hasnt rebooted in 10 days and try out a linux one.  Windows will be crawling while Linux is as fast as when it was booted.

Now certainly there are means by which you can speed up the boot process.  One of these is to disable anything that is loaded at startup that is not used.  Examples of this are things such as bluetooth and HP printer drivers.  These will not dramatically increase your boot up time though.  It is really not worth it.  What is 10 seconds?  Surely you do not have to boot up that often.

I have disable all of the stuff that i dont need, thats how i managed bootchart to show that my system loads in 20 secs. i do restart my desktop like 5 times in a day, as i said before, it seems that it takes to much to GDM to show me my login screen :confused:

---

### Post by p_quarles on 2007-07-30
> **pikul said:**
> I have disable all of the stuff that i dont need, thats how i managed bootchart to show that my system loads in 20 secs. i do restart my desktop like 5 times in a day, as i said before, it seems that it takes to much to GDM to show me my login screen :confused:
I'm not sure there's really that much you can do. You can try turning off unnecessary processes in Ubuntu, like Shae mentioned. You could also turn off Compiz and GDesklets, if you think that's slowing you down. 

If you're rebooting that frequently, though, you might just consider installing one of the OSes on a VM, so that you needn't be constantly switching between them.

---

### Post by pikul on 2007-07-30
> **p_quarles said:**
> I'm not sure there's really that much you can do. You can try turning off unnecessary processes in Ubuntu, like Shae mentioned. You could also turn off Compiz and GDesklets, if you think that's slowing you down. 

If you're rebooting that frequently, though, you might just consider installing one of the OSes on a VM, so that you needn't be constantly switching between them.

Thanks for your response :)

The thing its that it takes longer to show me the login screen, but it gives me excellent performance after i login to my session, i don't use Vista usually, the only time i use it its when i play games, i dont restart often (i said it wrong) what i do its shutdown my pc when im not using it :) and then turn it on when i do, and i do that like 5 times a day :)

---

### Post by bodhi.zazen on 2007-07-30
Well, you can also modify boot times by disabling services you do not need.

Also why is it a problem that Ubuntu boots slower then Windows ? It is not as if you should run Ubuntu over windows because of boot times.

If speed is your primary concern, well there are other distro's that are built for speed ... Arch Linux and Zenwalk come to mind ...

You can also see the various threads about speeding up ubuntu :

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

---

### Post by Patrick-Ruff on 2007-07-30
I'm having a hard time believing anything any of the people who have posted in this thread have said. except the poster above.

---

### Post by p_quarles on 2007-07-30
> **Patrick-Ruff said:**
> I'm having a hard time believing anything any of the people who have posted in this thread have said. except the poster above.
And that's relevant how?

---

### Post by pikul on 2007-07-30
I think nobody its reading my first post :lolflag: i have already disable everything i dont need,  post my bootchart, and i never said i was going to start using vista instead of ubuntu because its slower on boot times :lolflag: and i also said that it looks like GDM seems to be the problem, i read somewhere that there use to be a early login mod for GDM, but it didn't work, thanks anyways :)

---

### Post by bodhi.zazen on 2007-07-30
Well, you can always disable GDM and boot to the CLI, log in, type "startx"

What do you think is wrong with GDM ?

---

### Post by p_quarles on 2007-07-30
I read your first post, and I think most people did. What everyone is saying is simple: Ubuntu and GDM are working correctly. It takes about half-a-minute to boot. It takes longer than booting Vista with all startup programs disabled. There's very little you can do, short of swtiching to a lighter distro or using the CLI. 

I looked, and I can't identify any errors or hangups in the boot process you posted. If you're convinced there's some sort of problem (I don't believe there is, but that's just my opinion), then you should configure grub to boot in verbose mode and post the output here.

---

### Post by vexorian on 2007-07-30
I wouldn't really worry too much about 18 seconds, both loading times are less than 1 minute and that sounds blazing fast for me -) . 

So my recommendation is, if it is not broken don't fix it.

---

### Post by pikul on 2007-07-30
I don't exactly know why my bootchart says 20 secs but i get the login screen in 38 secs, i need to clear that out jajajaja thanks in advance :)

---

### Post by pikul on 2007-07-30
> **vexorian said:**
> I wouldn't really worry too much about 18 seconds, both loading times are less than 1 minute and that sounds blazing fast for me -) . 

So my recommendation is, if it is not broken don't fix it.

Thanks for your reply, i guess ill end up doing that or trying kde :KS  somebody said that it seems to be faster :)

---

### Post by shae on 2007-07-30
Bootchart measures the boot process where modules and services are loaded, however it does not measure any delays in GDM's input or the loading of Gnome through Gnome session.

---

### Post by pikul on 2007-07-30
ooooooooooooooo okay thanks, i guess theres nothing i can do then, i havent found any tips for improving GDM, if someone have any i would appreciate you posting them, maybe ill try kde, its anyone using it here ?

---

### Post by sigge on 2007-08-01
About boot times. It might be an improvement to compile a new kernel. It is rather technical, and I'm not feeling up to guide you thru it... I'm too noob. But someone else might...:guitar:
rock ON!

---

