---
title: "Changing computer name?"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Scintillement on 2006-07-28
When logging on to Ubuntu in the lower right corner of the screen it shows my computer name. Well the one I chose for it when I installed Ubuntu anyway. It says something like "Example-Laptop". I would like to know how to change that, if possible.

---

### Post by croak77 on 2006-07-28
The name is in /etc/hostname. Also take a look at /etc/hosts. And change your old name to your new one too.

---

### Post by steve.horsley on 2006-07-28
As croak77 says, the two files you need to edit are /etc/hostname and /etc/hosts. 
**BUT...** You must change both at the same time. If you change one, you will not be able to use the sudo command again until the other is also changed. 
So I suggest that you use the command **gksudo gedit /etc/hosts /etc/hostname**, edit both and save both.

---

### Post by Drakkor on 2006-11-08
Thanks,Steve, I wanted to do that also, Cheers ! :D

---

### Post by steve.horsley on 2006-11-08
Alternatively, System->Administration->Networking and the hostname is under the General tab. This is probably the safer way to change the hostname.

---

### Post by CatKiller on 2006-11-08
> **steve.horsley said:**
> Alternatively, System->Administration->Networking and the hostname is under the General tab. **This is probably the safer way to change the hostname**.

Given the number of "sudo doesn't work any more" posts, I think that's probably fair to say.

---

### Post by Drakkor on 2006-11-08
Huhh......just did sudo nano /etc/fstab and it works.........

---

### Post by ajm2005 on 2006-12-10
> **steve.horsley said:**
> Alternatively, System->Administration->Networking and the hostname is under the General tab. This is probably the safer way to change the hostname.

I used that method. then later, I inspected /etc/hosts and /etc/hostnames and found that the computer name had only been changed in one of them. I had to change the other manually. :-?

---

### Post by CatKiller on 2006-12-10
> **ajm2005 said:**
> I used that method. then later, I inspected /etc/hosts and /etc/hostnames and found that the computer name had only been changed in one of them. I had to change the other manually. :-?

Crikey. I've never seen that happen. It's probably worth filing that as a bug, if you can remember all the circumstances.

---

### Post by winsane on 2008-04-29
Hmm...I am using a fresh install of Ubuntu server 6.06 LTS and it didn't recognize gksudo as a valid command. Come to think of it, it didn't recognize gedit either. How do I get these commands to work? Is there a different way of doing this on server?

Sorry, not trying to sprout a new thread in the middle of this one.
These commands didn't work for me (gksudo and gedit)......
***In reference to steve.horsley post #3 above

---

### Post by bilal.17 on 2008-04-29
> **ajm2005 said:**
> I used that method. then later, I inspected /etc/hosts and /etc/hostnames and found that the computer name had only been changed in one of them. I had to change the other manually. :-?

same thing happened to me so I had to manually change them both, i recommend changing /etc/hosts and /etc/hostnames  manually at the same time better.

---

### Post by cybiko123 on 2008-04-29
> **winsane said:**
> Hmm...I am using a fresh install of Ubuntu server 6.06 LTS and it didn't recognize gksudo as a valid command. Come to think of it, it didn't recognize gedit either. How do I get these commands to work? Is there a different way of doing this on server?

Gksudo and gedit are graphical commands. Since the server edition doesn't have graphics, graphical commands are not available.

You can use sudo and emacs as replacements for gksudo and gedit, respectively.

---

### Post by beau.raines on 2008-06-22
I had the sudo didn't work right problem after just changing /etc/hostname and it remained after I changed /etc/hosts to match.

The solution to change them both simultaneously was the trick!


> **steve.horsley said:**
> As croak77 says, the two files you need to edit are /etc/hostname and /etc/hosts. 
**BUT...** You must change both at the same time. If you change one, you will not be able to use the sudo command again until the other is also changed. 
So I suggest that you use the command **gksudo gedit /etc/hosts /etc/hostname**, edit both and save both.

Thank you!

---

### Post by swtub on 2008-06-24
After making both changes at the same time I needed to reboot to allow the new, shorter, name to join a Windows domain (I probably didn't need to reboot but new to Ubuntu so just falling back on how I do things in Windows).

---

