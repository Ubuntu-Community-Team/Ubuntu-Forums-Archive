---
title: "Default username &amp; password"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by michaelof36 on 2006-12-03
I was never asked for a username and password during the installation of Ubuntu 6.10. Is there a default one? Or how do I add a username and password?

Mike

---

### Post by taurus on 2006-12-03
It's impossible!!!  Did you use the desktop CD/LiveCD or the alternate CD?  Boot into recovery mode from GRUB menu and at the prompt, paste the output of this command here!!!

```
cat /etc/passwd
```

---

### Post by aysiu on 2006-12-03
Did you, by chance, do the OEM installation?

Every other installation method will ask you for a username and password.

---

### Post by michaelof36 on 2006-12-03
I used the alternate cd I don't think I used the OEM option. But I did step away from my computer during the instillation if that helps.

---

### Post by taurus on 2006-12-03
It doesn't matter if you step away while installing it because it will not continue until you put in your full name, your username (or the computer picks one for you after you enter your full name, usually your first name), and a password.  So, what does /etc/password look like then?

```
cat /etc/passwd
```

---

### Post by michaelof36 on 2006-12-03
Its a mess of words I have no idea what they stand for. I created a username & pass but I don't have access to the full OS. How do I copy the contents of /etc/password to this forum, I had to boot into Win XP to access the internet correctly to post this

Mike

---

### Post by michaelof36 on 2006-12-03
What is it that I'm looking for?

---

### Post by taurus on 2006-12-03
I am looking for the last few lines in that file to see if there is a username that you've forgotten!!!

---

### Post by michaelof36 on 2006-12-03
Sorry I'll try and copy and paste

---

### Post by jonyboy1000 on 2006-12-03
I guess it's always possible to boot it up in a rescue mode (selcted from grub) and add a user from there as root.

There is an actual root in the rescue boot up.
It's all in command line so i think you have to go

useradd -m XYZ

(XYZ beign the user you wish to add)

---

### Post by davesmith on 2006-12-03
look, do i get this right? if i boot into recovery mode and type

cat /etc/passwd

is it going to tell me my supposedly secure password?

---

### Post by taurus on 2006-12-03
> **davesmith said:**
> look, do i get this right? if i boot into recovery mode and type

cat /etc/passwd

is it going to tell me my supposedly secure password?
NO.  Your password does **NOT** save in /etc/passwd.  Its stored in /etc/shadows and encrypted so you can't find out...

---

### Post by davesmith on 2006-12-03
\\:D/ a bit like this chip on my new passport then! whats in it i wonder?
i am relieved tho, one of the cool things about ubuntu is strong security

---

### Post by taurus on 2006-12-03
It's always like that in Linux/Unix...

---

### Post by davesmith on 2006-12-03
yep...i like linux...i never wanted or needed all the bloatware and backdoors and other security issues in the other OS

Is it possible to put a different password on a directory, so it positively cant be opened remotely?

---

### Post by taurus on 2006-12-03
You cannot view /etc/shadows as regular users.  Only root (or somebody with the sudo privilege) can view it and besides, it's encrypted so good luck trying to figure out the passwords...  I don't know why you are so concerned about it so much since people who run the big servers/machines don't seem to bother about it!!!

---

### Post by michaelof36 on 2006-12-03
I can't figure it out I'm just going to format and reinstall!!!!!!!!!:evil:

---

### Post by taurus on 2006-12-03
> **michaelof36 said:**
> I can't figure it out I'm just going to format and reinstall!!!!!!!!!:evil:
Okay, if that's what you want...

---

### Post by davesmith on 2006-12-03
Im new to this OS and its different to windows is why.

Windows is difficult to secure, protecting important data on windows while online is a nightmare

---

### Post by taurus on 2006-12-03
I have one word for you:  _**Windows**_.

---

### Post by michaelof36 on 2006-12-04
Yeah I'm used to Windows but then again, I'm really tired of all the headaches that its been giving me from time to time, I just want an OS that I can use that won't crash as often and isn't such a pain to maintain. The perfect OS...yeah right not in this lifetime! But I'm willing to give Ubuntu a second try, now that I know what to expect from it. ;) 

Mike

---

