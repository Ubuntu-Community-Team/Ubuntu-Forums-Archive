---
title: "Getting most of XP SP3"
date: 2011-08-10
forum: Any Other OS
---

### Post by gigenieks on 2011-08-10
Hi all,


I have installed on my ancient PC:
[LIST]
[*]CPU Celeron 1.8GHz
[*]RAM 768MB DDR
[*]GeForce 6200A (AGP)
[/LIST]
Xubuntu 11.04 and in Virtual Box XP SP3. Just that, no drivers, [COLOR="DarkGreen"]**no nothing.. yet!**[/COLOR] 
**First**, I want to seek some guidence from experienced and/or smart people (and this forum have plenty)

My goal and only goal is to use XP [COLOR="Purple"]**_for studies_**[/COLOR] (university; some windows programs).
I will know for sure that I will use these programs:
[LIST]
[*]MS Office 2007
[*]Pascal
[*]Mathematica
[*]Delphi
[/LIST]
later probably some others.. 

I **will not** use XP to browse net (I am thinking to disable any networking capability)
I **definetly will not** use for multimedia (listen music or watch movies / serials)

So, I want to disable, remove everything I could think of that I will not use. Services, registry tweaks, settings, unnecessary drivers etc etc 
You name it.

Anyway Virtual Box has nice feature: **snapshots**. => no worries if something goes wrong!

I just want it to be [COLOR="DarkRed"]**as [COLOR="Navy"]FAST[/COLOR] as it could possibly could!**[/COLOR] (later I will do that kind of stuff on *buntu too, I just need to set up XP **before my studies start** in few weeks)

[SIZE="4"]So, how one would advise to proceed? [/SIZE]
I havent even installed drivers, should I? (I don't know if I should; for example chipset driver, nvidia driver?, other?)

Hope I provided enough info about what I have and what I want.

---

### Post by mips on 2011-08-10
Start by stripping the install media down using nLite and build a new install CD.

With nLite you can remove all the languages you don't need, printer drivers, obscure networking protocols like banyan vines, atm, ipx/spx etc and a load of other stuff. There are plenty of nLite guides on the net. I got my install CD down to about 200MB.

You don't need drivers for XP when you install it in Virtualbox, all you have to do is install the Guest Additions from the Virtualbox menu. It does not use your normal hardware drivers when running in a VM, it uses the VB drivers.

---

### Post by wolfen69 on 2011-08-10
> **gigenieks said:**
> 
Anyway Virtual Box has nice feature: **snapshots**. => no worries if something goes wrong!
I just usually backup the virtualbox config file to an external hard drive. But whatever works for you.

> [SIZE="4"]So, how one would advise to proceed? [/SIZE]


I would try and get a little more memory if possible. Vbox demands it if you want to get good performance.

---

### Post by Johnb0y on 2011-08-10
> **mips said:**
> Start by stripping the install media down using nLite and build a new install CD.

With nLite you can remove all the languages you don't need, printer drivers, obscure networking protocols like banyan vines, atm, ipx/spx etc and a load of other stuff. There are plenty of nLite guides on the net. I got my install CD down to about 200MB.

You don't need drivers for XP when you install it in Virtualbox, all you have to do is install the Guest Additions from the Virtualbox menu. It does not use your normal hardware drivers when running in a VM, it uses the VB drivers.

> Start by stripping the install media down using nLite and build a new install CD.[http://lifehacker.com/374376/trim-down-windows-to-the-bare-essentials](http://lifehacker.com/374376/trim-down-windows-to-the-bare-essentials)

hope that helps. helped me a bit, it really differs to what you want exactly but its a rough guide anyway! :D

---

### Post by BrokenKingpin on 2011-08-12
> **mips said:**
> Start by stripping the install media down using nLite and build a new install CD.

With nLite you can remove all the languages you don't need, printer drivers, obscure networking protocols like banyan vines, atm, ipx/spx etc and a load of other stuff. There are plenty of nLite guides on the net. I got my install CD down to about 200MB.

You don't need drivers for XP when you install it in Virtualbox, all you have to do is install the Guest Additions from the Virtualbox menu. It does not use your normal hardware drivers when running in a VM, it uses the VB drivers.
This... plus:
- Disable themes and run the classic Win32 theme
- Disable the firewall and don't run any anti-virus (only if you are keeping it off the network)
- Disable any startup services that are not needed

That should keep it light enough. You could keep it even lighter if you kept it on XP SP2... and if you are not going to have it on the network you would not need all the security patches from SP3. I find after upgrading XP from SP2 to SP3 it is noticeably slower.

---

### Post by Dr. C on 2011-08-13
Have you considered getting some additional RAM for your PC? Both Xubuntu and XP. will love you for it. From the vintage of the PC I am guessing it will take up to 1.5GB and that will make a huge difference.

---

### Post by gigenieks on 2011-08-14
> **mips said:**
> Start by stripping the install media down using nLite and build a new install CD.

Yes I am doing that. (have problem, see link in the end of post) :rolleyes:

> **wolfen69]
I would try and get a little more memory if possible. Vbox demands it if you want to get good performance.[/QUOTE]
Yes, of course. 
In coming days I will know what computer I will have. (friend is testing if my Pentium 4 3.4GHz is working or not said:**
> [http://lifehacker.com/374376/trim-down-windows-to-the-bare-essentials](http://lifehacker.com/374376/trim-down-windows-to-the-bare-essentials)

hope that helps. 
Helped a lot! Thank you. :rolleyes:


**[COLOR="Purple"]Ooo thank you BrokenKingpin![/COLOR]** Yes, I am planning on [COLOR="DarkRed"]**not using any network capabilities**[/COLOR] on that XP, just some windows applications.. ;)
Hmm, seems if I will not use network (go internet) SP2 is right service pack for me, right? 
Again tnx.

> **Dr. C said:**
> Have you considered getting some additional RAM for your PC? Both Xubuntu and XP. will love you for it. 
Yes, I am quite sure about getting more RAM. I want to have 2GB (I have a habit of opening like 30 to 50 tabs in web browser :D)

[COLOR="DarkRed"]**Guys need help in my other thread**[/COLOR] so I could try that nLite installation --->
[[COLOR="Blue"]make .iso from folder[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1824768")

---

### Post by gigenieks on 2011-08-14
bump

---

### Post by PCaddicted on 2011-08-14
[QUOTE=BrokenKingpin]This... plus:
- Disable themes and run the classic Win32 theme
- Disable the firewall and don't run any anti-virus (only if you are keeping it off the network)
- Disable any startup services that are not needed[/QUOTE]
+1 and remember to disable menu transitions:

[LIST=1]
[*]click the right mouse button on the desktop and then click Properties.
[*]In the Properties window of the display, open the Appearance tab.
[*]Click the Effects button.
[*]Then uncheck the Use the following transition effect for menus and info bubbles.
[*]OK.
[/LIST]
Also, disable visual effects. See:[http://teamtutorials.com/windows-tutorials/disable-visual-effects-to-speed-up-windows-xp](http://teamtutorials.com/windows-tutorials/disable-visual-effects-to-speed-up-windows-xp).

[RIGHT]  [URL="http://forums.techarena.in/newreply.php?do=newreply&p=4181233"]
[/URL]  [/RIGHT]
[QUOTE=BrokenKingpin]That should keep it light enough. You could keep it  even lighter if you kept it on XP SP2... and if you are not going to  have it on the network you would not need all the security patches from  SP3. I find after upgrading XP from SP2 to SP3 it is noticeably  slower.[/QUOTE]
Agreed. For the purpose desired by the OP,  performance is more important than security. Don't fit your Windows installation with any security tools/patches, you obviously don't need them.  

And, when installing a program that *you need*, remember not to install any useless additional toolbars/programs etc that the installer offers. Do not make a Desktop icon for the program, but only a QuickLaunch icon, in order to keep your desktop clean.
  [RIGHT]  [URL="http://forums.techarena.in/newreply.php?do=newreply&p=4181233"]
[/URL]  [/RIGHT]

---

### Post by gigenieks on 2011-08-14
[QUOTE=PCaddicted]
Agreed. For the purpose desired by the OP,  performance is more important than security. Don't fit your Windows installation with any security tools/patches, you obviously don't need them.
[/QUOTE]
First, what is "OP"? :confused:
Second, so the best approach is to install XP with SP2, right? 

> 
And, when installing a program that *you need*, remember not to install any useless additional toolbars/programs etc that the installer offers. 

Of course!

Thank you for your suggestions! :)


P.S. still need help in other thread, I can't really start trying this stuff, see details here --->
[http://ubuntuforums.org/showthread.php?t=1824768](http://ubuntuforums.org/showthread.php?t=1824768)

---

### Post by PCaddicted on 2011-08-14
> **gigenieks said:**
> First, what is "OP"? :confused:

Original poster. The person who started the thread.
> Second, so the best approach is to install XP with SP2, right?  
Yes. SP3 does not have better performance than SP2, but it has heavier security thus it runs slower. And you're pursuing performance not security.

---

### Post by gigenieks on 2011-08-14
OK I have quite a things to do, IF only I could start installing my nLite XP version...

---

