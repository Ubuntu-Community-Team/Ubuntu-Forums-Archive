---
title: "voice module for grub?"
date: 2008-08-17
forum: Assistive Technology &amp; Accessibility
---

### Post by alzie on 2008-08-17
Is there a way to have grub announce ubuntu or windows?  

Is there a way to have have user name and password announced?

I tried to help in a Wubi forum with a poster who is blind.  They had gotten to grub but were stuck.  They couldn't see to select ubuntu.

Then I realized that after you find ubuntu you have to wait to enter the username and password.  This time will vary by machine.

Is there a sloution already in place that I can't find?  Or is this something to be passed on for inclusion in 8.10 or 9.4?  If it is do-able.

Thanks for your interest.

---

### Post by Sef on 2008-08-17
> Then I realized that after you find ubuntu you have to wait to enter the username and password. This time will vary by machine.

Is there a sloution already in place that I can't find? Or is this something to be passed on for inclusion in 8.10 or 9.4? If it is do-able.

Ubuntu will automatically be chosen after some seconds.  (20 I think.)

To boot directly into Ubuntu is possible:

System > Administration > Login Window > Security > Click on 'Enable Automatic Login' > Set to desired user to login automatically

---

### Post by alzie on 2008-08-17
Thanks for the reply.  The reason I asked is if I noticed this issue then others must have too.  I was hoping there would be a fix around that I haven't come across yet.

The default with Wubi is Windows and I think the timeout is about 10 seconds.

I think you can disable the timeout using startup manager too.

If I select "run at start" for Orca in preferred applications would Orca start before the username/password  prompts?

I think I need to set up a test wubi on my computer.

---

### Post by Sef on 2008-08-18
> The default with Wubi is Windows and I think the timeout is about 10 seconds.

That is correct.  GRUB would have to be changed, so Ubuntu would boot up first.  Check the Illustrated Dual Boot's '[Windows Operating System Entries]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")'.

---

### Post by alzie on 2008-08-25
I did find that an audio cue can be played at the login prompt using "login window" in the administration menu.

I sent a request to gnu.org asking about audio prompts for grub. I don't know if it will do anything but it never hurts to ask.

Thanks again for your time Sef.

---

### Post by voltagex on 2008-08-29
Audio isn't something GRUB would be capable of, but I'm happy to be proven wrong.

The following snippet of info might be helpful:

"One of the things LILO can do, is print a customized message before giving the prompt (that is the "boot" prompt, not the "LILO" prompt). Just put a line in your lilo.conf that looks like: message = /boot/message and put your customized message in /boot/message. The interesting thing is that if that file contains an ASCII 7 character (control-G), you will here a short beep when the message is actually printed by LILO. So when you hear that beep, you know you can release the shift key and type in your command line. "

That's for LILO, but GRUB should be able to have a similar message.

Sorry for not being more help, but it's 4:51am here...

---

### Post by McLogic on 2008-09-16
Grub has to be really small, and has to load fast. I doubt it would ever support audio.

The best result might be to find programs for all OS's used to change the next boot before logout by voice.

---

