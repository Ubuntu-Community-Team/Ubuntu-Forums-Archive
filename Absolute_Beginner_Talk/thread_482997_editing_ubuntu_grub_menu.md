---
title: "editing ubuntu grub menu"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by davenom on 2007-06-24
Hi, i'm an absolute noob when it comes to linux. Its taken me a few days to get ubuntu (7.04) up and running:D

Problem is, when i start my computer and it loads grub,it shows me a bunch of things which are unnecessary. Now from google i have found that i have to edit the grub file but i'm not sure how. I went to the grun folder and edited a file from ther but when i tried to save it it didn't lat me - only let me save it somewher else with a different name. How do i make the file editable?

Sorry if its obvious or if i'm making an obvious mistake (its my first few days of linux)

Thanks in adavnce

---

### Post by atria on 2007-06-24
It is located in /boot/grub/menu.lst

After editting execute grub-install

Be careful and don't break your boot loader ;)

---

### Post by davenom on 2007-06-24
Yes, but how exactly do i do that. Like i said when i navigate to the menu.lst  file in ubuntus file explorer it doesn't let me save the edited changes. And how do i execute grub-install?

---

### Post by atria on 2007-06-24
Oh oh i'm sorry i misunderstood you.

```
gksudo gedit /boot/grub/menu.lst
```
 or if you like the commandline better,
```
sudo nano -w /boot/grub/menu.lst
```

---

### Post by shen-an-doah on 2007-06-24
Try GrubEd: [http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

It lets you edit Grub in a nice graphical way, plus some other stuff...

---

### Post by logos34 on 2007-06-24
> **shen-an-doah said:**
> Try GrubEd: [http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

It lets you edit Grub in a nice graphical way, plus some other stuff...

I'd be leery of that application.  I tested it out (I was in Suse 10.1 I believe) and nearly deleted my entire grub menu.lst!  Couldn't believe it.  And I'm not some click-happy rookie windows user!  (Maybe it was just a bug in the version I tried).  

It's not much more difficult to just use gedit text editor.

---

### Post by shen-an-doah on 2007-06-24
> **logos34 said:**
> I'd be leery of that application.  I tested it out (I was in Suse 10.1 I believe) and nearly deleted my entire grub menu.lst!  Couldn't believe it.  And I'm not some click-happy rookie windows user!  (Maybe it was just a bug in the version I tried).  

It's not much more difficult to just use gedit text editor.

Really? It's not an app, it's a script really... Its back-up option is pretty important in cases like that. You could just as easily mess up your grub by editing it yourself...

---

### Post by logos34 on 2007-06-24
> **shen-an-doah said:**
> Really? It's not an app, it's a script really... Its back-up option is pretty important in cases like that. You could just as easily mess up your grub by editing it yourself...

there's sudo cp men.lst menu.lst_backup too.  easy.  Besides, at some point you're going to have to edit some configuration file by hand...there isn't a gui for everything.  Might as well do it by hand...its good practice.

---

### Post by shen-an-doah on 2007-06-24
> **logos34 said:**
> there's sudo cp men.lst menu.lst_backup too.  easy.  Besides, at some point you're going to have to edit some configuration file by hand...there isn't a gui for everything.  Might as well do it by hand...its good practice.

Well yes, but it doesn't hurt to give other options.

Also, I'm amazed no one mentioned that you should back-up before changing anything...

Just so anyone knows:

```
sudo cp menu.lst menu.lst_backup
```

Run that in a terminal before doing *anything* to your menu.list

Then if anything goes wrong:

```
sudo cp menu.lst_backup menu.lst
```

To go back to what it was before.

---

### Post by kwalters on 2007-06-24
I am having exactly the same problem as Davenom.  I have got ubuntu 7.04 running and dual booting with Windows XP.  But I want to change the default OS in GRub to number 4 (Win XP).  I too used the text editor to change the default from 0 to 4 but was not allowed to save the changes

I keep seeing screens which tell me I cannot do things because I am not the "owner"  (despite the fact that I think I am  - there are no other users).  It wont let me log on as "root" and if I use sudo before the command I still get told I do not have the permissions.

So  Question 1:  how do I get to be owner and therefore omnipotent?

Question 2  Could someone give me the complete idiot beginner's guide with every keystroke required to set my grub default to 4.  I start in a terminal window with my own username and a dollar sign.  How do I get the hash sign to appear?

Life would become a lot easier if I could crack the bootloader default problem.  I could  then start addressing more demading problems like how to get on line when Ubuntu did not recognise the Belkiin Wireless G USB device that would allow me to go online.

kw

---

### Post by davenom on 2007-06-24
Thanks alot guys. I've done it, and without messing it up.

---

### Post by logos34 on 2007-06-24
> 
kwalters 

Question 2  Could someone give me the complete idiot beginner's guide with every keystroke required to set my grub default to 4.  I start in a terminal window with my own username and a dollar sign.  How do I get the hash sign to appear?

$ **sudu -i**  (to become root)

For grub:
> **default   3**

(grub start counting at 0)

If windows is the 4th 'title' line (not hashed out) down starting from the first ubuntu kernel, then the above should work.  Or use
**> default   saved**

and if your windows entry has a **savedfault** option it will boot that.

---

### Post by Tomosaur on 2007-06-24
> **logos34 said:**
> I'd be leery of that application.  I tested it out (I was in Suse 10.1 I believe) and nearly deleted my entire grub menu.lst!  Couldn't believe it.  And I'm not some click-happy rookie windows user!  (Maybe it was just a bug in the version I tried).  

It's not much more difficult to just use gedit text editor.

How do you 'nearly' delete something?

---

### Post by kwalters on 2007-06-24
Thanks to those who responded, I have now solved my problem in editing the Grub default OS

The trick of putting **sudo -i** was really useful  (not **sudu -i** which was a typo)

I tried entering **default 4** from that root prompt and it did nothing.  I then entered **grub** and at the **grub>** prompt I tried **[/default 4B] and [B]grub-set-default 4** as per the on screen help.  Nothing worked so I went (as root) to **nano -w /boot/grub/menu.lst** and that put the file on screen.  I changed the number after default to 4 and then tried to work out how to save the change.  Eventually, when I decided to exit, I was offered a choice of saving it and it all worked as I wanted from then on

May I just say as a rookie, that a few contributors need to look hard at the title of this forum and the words "absolute beginners" and then think again about how clear their suggestions might be to absolute newcomers

KW

---

### Post by logos34 on 2007-06-24
sorry, kw, about the 'sudu' typo.  I usually try to be careful when it comes to the commands.

Seems I didn't fully appreciate your absolute beginner status. You said you used a text editor to open menu.lst, and even knew the line you were looking for so I figured you could do 

$sudo -i
#gedit /boot/grub/menu.lst  (Isn't this what you used to open it the first time?)

It's obvious to most everyone how to save changes (same as any other OS's text editor) so I don't even mention it

---

### Post by Nekiruhs on 2007-06-24
You could also do sudo su instead of sudo -i.

---

