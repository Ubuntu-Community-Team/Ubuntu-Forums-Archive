---
title: "Newbie of the n00bs"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by Qnaga868 on 2006-01-08
Hello and how are you.   
  I have some problems with ubuntu, I just installed Ubuntu this morning, and have been messing around with it all day. after reading for an hour on the forums i found out about the termal, and found some install guides, for rar.gz's i think they're called, and a install guide for the newest wine, and have it in my home folder. and i cant copy anything into file system, for i do not have permissions... what the heck??? OH and another thing is, the computer i installed Ubuntu on, is NOT connected to the internet, possibly this is a problem. but for now thats how its got to be. so i've tried quite a few things already, spent all day trying to install wine 0.9.5, and automatix. But in a nutshell im having problems installing wine and automatix, and maybe automatix wont recognize where wine is. If i need to and how do i tell synaptec where the wine files/folders are? please help, i've tried the guides from this forum already, and nothing will solve the problem of trying to get windows based programs running... thanks for your time
rob

---

### Post by Arktis on 2006-01-08
Welcome and good luck getting acquainted with Linux.

1.) You're not supposed to be able to change anything in the base file system unless you've got root.  It's for safety reasons.  You can make all the changes you like in your home directory, install apps there, edit configs, etc.  Make yourself a menu entry with smeg that uses the command **gksudo 'nautilus --no-desktop'** if you want be able to open a root file browser and make changes to /, but /home/your_username should be enough unless you're trying to make system wide changes.  Don't dare screw around with anything in / unless you're pretty sure you know what you are doing!

2.) I'd be happy to help you understand the basics of installing stuff.  You shouldn't be using things like automatix.. it's the cheap shortcut way and has it's issues.

3.) What do you use for networking/internet?  Ethernet, dial-up modem, wireless?

---

### Post by Terry of Astoria on 2006-01-08
You might try being a little more specific. 
I think Automatix is pretty much made to download stuff straight from the internet. What exactly are you trying to do? Have you been able to get wine installed?

---

### Post by Qnaga868 on 2006-01-08
I do not have any connection to the internet on the computer that Ubuntu is installed on. No i have not been able to install Wine yet, i followed the terminal command install guide, but ./configure did not work, after that i was lost... i'll read the guide you gave me, thanks, more help would be great.

---

### Post by blair on 2006-01-08
First of all, a suggestion: You have like 10 different issues/problems/assistance requests in the same thread. It makes it difficult to understand your situation and even more difficult to assis. Recommend you try to limit it to 1 issue per thread until you get it resolved and then move on to the next. Not trying to flame, just trying to make it easier for others to help you. 

1. I don't know your Linux experience level, but you mention that you just discovered the terminal which implies you are a newbie. If so, I recommend you pass on messing with Wine until you have a bit more experience. It is not for the faint of heart. Some people have luck with it, most don't  without a lot of tweaking. You need to know what you are doing. Alternatively, buy Crossover Office so you will have professional paid support. Most major apps have Linux versions, making the need to run a Windows app moot. 

2. You need to have appropriate permissions to copy and move files. Root of course does. The suggestion above will work. Alternatively:

1. Open a terminal via Applications > Accessories > Terminal
2.	Enter the following command: sudo passwd 
3.	You will be prompted for a password. Enter your *user* account password, not the root password. This is required to authenticate you to the system before it will let you establish the root account. The OS is basically authenticating you (via your password) before it will allow you to perform a root-level function; in this case establishing the root password.
4.	You will then be prompted to input a new root password twice. Enter your *new root password* two times.

You now have a separate root account set up.

The root account *by default* is not permitted to login into the desktop from the boot screen.  To enable root to login to their own desktop, just as any other user logs into their desktop:

1.	Log in from first system account (i.e. not other guest accounts that were subsequently set up on machine). You will be prompted for your password; Enter the first user account password, not the root password.
2.	System > Administration > Login Screen Setup > Security tab > Enable Allow root to login with GDM
3. Save changes. Close the dialogs. Log out. Log back in as user ID=root, password=the root password you just created. Now you have a normal desktop, full files access and complete control over the system. Just remember to log back out of the root account and log back in as a normal user once done making the necessary config changes. 

Also remember that the root account gives you complete, unrestricted ability to completely hose your system if you don't know what you are doing. Be prepared to learn from your mistakes and if you get uncontrollably lost, simply reinstall. Consider your Ubuntu PC an unstable sandbox for a few months as you make mistakes, reinstall and learn. 


3. Not having a network connection shouldn't stop you from initially installing but it will prevent you from downloading security patches, bug fixes and new packages. You should really have a network connection. 

4. Regarding Automatix, I'm familiar with it but have never had a need for it. The Synaptic package manager bundled with Ubuntu has satisfied every s/w download problem I've thrown at it. Make sure you have a really good reason for installing a software install tool when you already have one as part of your distro that is already optimized for the software that works with your distro.

5. You can't control where Synaptic installs files. That's the point. Each package already has install instructions built into it that get executed automatically so you don't need to know the details of where/how to install. Once installed, run the whereis command from a terminal to find out where the executable is hiding, e.g. "whereis wine".  If you want to configure Synaptic to download the wine package, there is one already in the Ubuntu repositories. Scroll through the packages list for wine and you will see it. If you want a more up to date version, one not officially supported by Ubuntu, so you take your chances, go to the winehq.org web site for instructions on how to find the latest package (still pre v1.0 and hence still considered an unstable beta. Use at your own risk). 


good luck. hope this info helps.

---

