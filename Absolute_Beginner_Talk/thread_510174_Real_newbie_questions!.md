---
title: "Real newbie questions!"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by John Macnab on 2007-07-26
Hi
I have some nutty newbie questions.:p
1.I started reading about linux and came across "type in your X window system..." . Now and X window system is something like kde and gnome isnt it?
2.One lesson talked of lilo.conf in /etc directory- But I couldnt find that one in my Ubuntu.Is it hidden or something?
3.I wouldnt be able to install Aptoncd program from the Aptoncd CD itself would I?
4.I just copied the packages I d/lded into a CD using Aptoncd but what when I download more?How do I find out which ones I downloaded afterwards since everything goes into one single folder?
5.My first account that I create when I install Ubuntu is the root isnt it?But in the users&groups menu it lists another 'root'!
6.If I make a user account, every time I want to install something or change something I will have to log in as my root account wouldnt I?
7.Does anyone use a Yahoo chat client with voice capability?
Sorry for the multitude of questions, if it is not allowed, I'll post them separately. Please do advise

---

### Post by LaRoza on 2007-07-26
> **John Macnab said:**
> Hi
I have some nutty newbie questions.:p
1.I started reading about linux and came across "type in your X window system..." . Now and X window system is something like kde and gnome isnt it?
2.One lesson talked of lilo.conf in /etc directory- But I couldnt find that one in my Ubuntu.Is it hidden or something?
3.I wouldnt be able to install Aptoncd program from the Aptoncd CD itself would I?
4.I just copied the packages I d/lded into a CD using Aptoncd but what when I download more?How do I find out which ones I downloaded afterwards since everything goes into one single folder?
5.My first account that I create when I install Ubuntu is the root isnt it?But in the users&groups menu it lists another 'root'!
6.If I make a user account, every time I want to install something or change something I will have to log in as my root account wouldnt I?
7.Does anyone use a Yahoo chat client with voice capability?
Sorry for the multitude of questions, if it is not allowed, I'll post them separately. Please do advise

0. X is what GNOME and KDE are running on top of.
1. LILO is a boot manager, Ubuntu uses Grub, which is easier to use.
2. I am unfamiliar with "Aptoncd", but Ubuntu comes with apt and aptitude
3. n/a 
4. No, your account is not root, you will have to explicitly run programs as root, this is a very secure system
5. DO NOT LOG IN AS ROOT, only run commands and programs as root when necessary.
6. n/a

-EDIT to run something as root, type "sudo" before the command name, if it is a command, or type "gksudo <appName>" in the terminal for graphical apps.

---

### Post by thefoolisme on 2007-07-26
Answer to #6 cont. 

No, you don't have to log in as root every time you want to install something.  If you use add/remove programs or Synaptic Package Manager, they will just ask you for your password before installing.  you don't have to worry about logging out and in.

---

### Post by John Macnab on 2007-07-26
Thnak you for the replies :)
Oh gawd I am confused here.LaRoza, sir,when I was installing Ubuntu, it made me create an account and I was under the impression that was the root account.But it is not? It is just an admin account?And I wont ever need the real root account for anything I hope?So what do people mean "never use Linux in root account mode all the time"? I mean you dont create or know the root account password anyway?I created only one single account on this machine uptil now, so I can continue using that?*eeek I do sound confused dont I? sorry*

Thefoolisme, sir,I just created a second account but when I try to start firestarter it asks me for the password I use for administrative tasks- and I put in the same password I used to put in for synaptic and in the console (in my first account)but it keeps saying "incorrect password, try again". And it's confusing me. Please , do clarify a bit?

---

