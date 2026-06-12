---
title: "Password Error"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Vuto on 2007-07-28
Whenever I try and open a program that needs the administrator password I get this message after I type in the password
> Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

And after that message has appeared once the program won't start again

Could someone please tell me what is happeneing?

---

### Post by pyros on 2007-07-28
Are you in the account that you created when you were installing ubuntu? if not, you need to be added to the sudo list. If you are, then you might not have been added to the admin group like you were supposed to. to fix that, boot off of your install cd and go into recovery mode. follow through the steps, once you get to a command prompt, type ```

addgroup username admin

```
where [FONT="mono"]username[/FONT] is whatever you use for a login name.

---

### Post by Vuto on 2007-07-28
what do you mean by boot off and could you make it more detailed please I am very new to ubuntu

---

### Post by candtalan on 2007-07-28
I think 'boot off the cd' means you to use the live CD which you probably used to initially run and install ubuntu, using the machine with this CD again now, and putting the CD in and then starting the machine, and booting from the CD.

Then you find you are running the machine, but using the CD software not the installed files. It means you can easily change the installed system while it is asleep..... :-)

Does that explain things? If not please ask again?

---

### Post by Vuto on 2007-07-28
I dont have a cd my dad's friend installed this for me

---

### Post by Koybe on 2007-07-28
It seems that you're not using an admin account. That's what pyros try to tell you.

So you do not need the cd, Anyway, during the installation, you should (or someone else) have created a user. That user has admin rights, which means he can add you to the admin group and you'll be able to type your password and access the menu.

So you should log in with that account, go in System -> Administration -> Users and Groups, then there you can add you current user to the admin group. Or simply typing the command pyro gave you before.

---

### Post by Vuto on 2007-07-28
well this is the root use account but I changed the account name and password by changing the accoutn name does that matter?
whn i type in pyos's command i get this
> addgroup: Only root may add a user or group to the system.

---

### Post by Koybe on 2007-07-28
You should not rename 'root' user. You can use set a password if you want but not rename it.

---

### Post by nanie on 2007-07-28
I often meet the same problem~~maybe  something wrong with Internet

_____________________________
tomorrow is another day
**[dvd to iphone](http://www.dvdtoiphone.org/)**

---

### Post by Vuto on 2007-07-28
so what do i do now?

---

### Post by Koybe on 2007-07-28
I'm not sure what you are able to do.

Could you post your /etc/passwd file to be sure what you renamed or not?

Then we'll try to make it as it was at the beginning.

---

### Post by spiderbatdad on 2007-07-28
Burn your own iso from ubuntu's distribution site and start yourself off from scratch.

---

### Post by pyros on 2007-07-28
There seems to be a bug in the installer, as this is the third time I have encoutered this on the forums. The user that is created when you install ubuntu should be a member of the admin group, but, based on the error that you are recieving, it would appear that this did not happen.

This can be fixed by using the installation cd to enter recovery mode. I thought that both the desktop and alternate install cds had this, but it appears that it is only on the alternate install cd. If you have a cd burner on your computer, download this file: ([7.04](http://mirrors.easynews.com/linux/ubuntu-releases/7.04/ubuntu-7.04-alternate-i386.iso)) and burn it to disc. If possible, tell your dad's friend about this thread, and he can help you.

Once you boot off of the cd, there is an option on the first menu that you will see, called "Rescue a broken system" that will (eventually) give you a root command prompt where you can run the addgroup command. After you do that you just have to type reboot, take the cd out and let ubuntu start up normaly.

---

### Post by Vuto on 2007-07-28
I don't have a cd burner is their any way that i could just start from scratch again?

---

### Post by meierfra on 2007-07-28
I don't think there is a reason to reinstall. But you need to give as some more information to figure out what really happened. 

Type
```
gedit /etc/passwd
```

in the terminal and post the output ( don't worry this file does not contain any passwords, but it does list all the users)

---

### Post by sumguy231 on 2007-07-28
> 
This can be fixed by using the installation cd to enter recovery mode. I thought that both the desktop and alternate install cds had this, but it appears that it is only on the alternate install cd. If you have a cd burner on your computer, download this file: (7.04) and burn it to disc. If possible, tell your dad's friend about this thread, and he can help you.
Wait, maybe I'm missing something, but why not just reboot, hit Esc to enter the Grub menu, and boot with the 'recovery mode' option? That'll get you to a root console just fine.

---

### Post by pyros on 2007-07-28
> **sumguy231 said:**
> Wait, maybe I'm missing something, but why not just reboot, hit Esc to enter the Grub menu, and boot with the 'recovery mode' option? That'll get you to a root console just fine.

"DOH!" 
Well, yeah, I suppose you could do that...

---

### Post by meierfra on 2007-07-28
Yes, but I think his  user accounts are screwed-up and should be fixed.

---

### Post by pyros on 2007-07-29
> **meierfra said:**
> Yes, but I think his  user accounts are screwed-up and should be fixed.

Right, that's the idea... but if the problem is that you can't gain admin privleges, you can't really fix it. Hence the need for recovery mode and the super user prompt.

---

### Post by Vuto on 2007-07-29
where is the grub menu? maybe his way could work?

---

### Post by Koybe on 2007-07-29
It's at boot. Just press 'e'. But as far as you go I think it would be easier for you to restart from beginning. Everything would already be completed for now ;)

---

### Post by Vuto on 2007-07-30
u didn't tell me where it is where is boot?

---

### Post by Vuto on 2007-07-31
ok i got it working i added myself thru the grub menu

After it finished recovering i typed in pyros's cmd
> addgroup "username' admin
restarted my computer then it worked

Thank you all that helped!

---

