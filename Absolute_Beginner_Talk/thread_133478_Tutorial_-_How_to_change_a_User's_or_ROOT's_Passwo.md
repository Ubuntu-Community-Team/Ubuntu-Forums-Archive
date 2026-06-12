---
title: "Tutorial - How to change a User's or ROOT's Password before Booting"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-20
Hello ALL !!!

Since I like Ubuntu so much (& learning at the same time), I will give you this nice Tutorial regarding the:


_How to change a User's or ROOT's Password before Booting_:

To Log in in your Ubuntu, simply use your "user name" (you gave during the installation) & the "password" (you specified at that time).


If you have Forgotten your User's "password":


There are two ways to go on this:

1. To Change your current User's Password:

    a. Restart Ubuntu in Recovery Mode (at the Boot Menu select your Kernel & 
        "Recovery Mode" which will get you to the Command Line (the bash Shell's $ 
         or # prompt).

    b. Type:

	passwd <username>

    c. Enter a NEW "password".

    d. Then Reboot (using "reboot") your Ubuntu & Log in with your "username" & 
        the NEW "password" you specified.

2. To Create a NEW User Account:

    a. Boot Ubuntu in Recovery Mode (at the Boot Menu select your Kernel & 
        "Recovery Mode" which will get you to the Command Line (the bash Shell's $ 
        or # prompt).

     b. Type:

	useradd -m new_user_name

     c. Type:

	passwd new_user_name 

     d. Enter the NEW User's Password twice.

     e. Then Reboot (using "reboot") your Ubuntu & Log in with your NEW 
         "username" & "password" you specified.

IF Ubuntu does NOT let you type ANY of the above commands & requests a ROOT Password, do the following:

    _Note_:
    By default, there is NO "root" Password in Ubuntu (the ROOT Password is NOT 
    set).
    Once you Set a ROOT Password in Ubuntu, it requires it when you are in the 
    "Recovery Mode".
    You can use an Ubuntu Install CD to Reset the ROOT Password.

1. Insert the Install CD & at the CD Boot Prompt, type:

	rescue

2. Follow the instructions & when you are in the "Terminal", type:

	passwd root

3. Enter the ROOT Password twice in there & Add a NEW User account with:

	adduser

4. Enter your NEW User info & when your finished, type:

	adduser your_new_user_name admin

    _Note_:
    This is performed so that the NEW User can access System Tools as ROOT.

5. Then remove your InstallCD, Reboot (using "reboot") your Ubuntu & Log in with 
    your NEW User account.

---

### Post by majikstreet on 2006-02-20
I have made something similar to this in the Customization Tips and Tricks forum. 

Yours has tons more info :)

Can you reply to my thread with this info? It'd be nice :)

[http://ubuntuforums.org/showthread.php?t=133102](http://ubuntuforums.org/showthread.php?t=133102)

thanks,
majikstreet

---

### Post by dvarsam on 2006-02-20
[QUOTE=majikstreet]
I have made something similar to this in the Customization Tips and Tricks forum. 

Yours has tons more info :)

Can you reply to my thread with this info? It'd be nice :)

[http://ubuntuforums.org/showthread.php?t=133102](http://ubuntuforums.org/showthread.php?t=133102)

[/QUOTE]

Thanks for your good words & reply.

What I do is watch this Forum & read a lot of articles (with user's problems).

Then I blend everything into 1 version.

_Note to Everybody_:

Every now & then I create some Tutorials.

I want to be able to Post them Somewhere on the Internet to be available to the Whole Ubuntu community.

Does anybody maintain any Web page - so I can mail him some files to post?

Cause I do not know how to Post stuff...

Thanks.

P.S.> By the way, I will blend your article into mine, cause I am missing some stuff that you state & I will then create a better version.

---

### Post by majikstreet on 2006-02-20
That's nice.

Well, you could post stuff here on the forum, in say the tips and tricks forum, or on the wiki: wiki.ubuntu.com .. it has a fairly easy syntax to learn and it's pretty easy to post stuff there, too.

---

### Post by kvorion on 2006-02-20
This is similar to how we change the root password in other distros like Fedora (by booting into linux single mode)

 I am wondering, how could you protect your system from someone intentionally changing your root pass or user pass? For one thing I guess you could set a bootloader password. Anything else? Doesnt it sound a bit too easy to get root privileges on the box after reading these tutorials?

---

### Post by dvarsam on 2006-02-20
[QUOTE=majikstreet]That's nice.

Well, you could post stuff here on the forum, in say the tips and tricks forum, or on the wiki: wiki.ubuntu.com .. it has a fairly easy syntax to learn and it's pretty easy to post stuff there, too.[/QUOTE]

Well if you visit the Ubuntu's "Customization Tips & Tricks", link below:

[http://www.ubuntuforum.org/forumdisplay.php?f=100](http://www.ubuntuforum.org/forumdisplay.php?f=100)

... you will find that there is TOO many diff stuff blended (mixed) in there...

How can I send an e-mail to the "administrators" of this Ubuntu Forum (you know: the people who maintain this Forum) & ask them to categorize the "Customization Tips & Tricks" Folder?

Because I want to write on how to do the "Basics" & the people who post in there, instead of the "Basics" (some) describe _TOO_ complicated stuff.


The Ubuntu administrators _MUST_ create separate folders in there:

1. "Beginners" & "Basics" or "How to Start".

2. "Advanced"

Also some categorization" e.g. Network, Microsoft Windows Related, Security & Antivirus, e.t.c.

The "Basics" that I want to put in there, do NOT blend in....

Please Help...

---

### Post by jjf on 2006-02-20
[QUOTE=kvorion]I am wondering, how could you protect your system from someone intentionally changing your root pass or user pass? For one thing I guess you could set a bootloader password. Anything else? Doesnt it sound a bit too easy to get root privileges on the box after reading these tutorials?[/QUOTE]

My thought exactly.  This means anyone with a little bit of know-how and physical access to my box can easily boot into recovery mode, set my password, and log in to my account!

So let me ask the pros: Do you guys set a root password to prevent this from happening?  Does setting a root password break mess up sudo, or no longer accept your first user's password to run Synaptic, etc?

---

### Post by dvarsam on 2006-02-20
I agree with you Totally !!!

It is NOT good for ANYBODY that knows your username, to be able to change YOUR Username's Password & access _all_ YOUR files with YOUR user rights. :( 

It would be better, if Ubuntu FORCED you to Boot as Root (in such a case).:-k 

So, if you are concerned with Security it is good to create a Root account.

This way, if somebody wants to break in YOUR PC:

1. They need to know your root Password,

OR:

2. They need to Boot from CD & change your Root Password from there :mrgreen: 

In the 2nd case, you MUST Restrict Ubuntu to Boot from a CD.;) 
So, enter the BIOS & do NOT let Ubuntu Boot from a CD.
Then secure your BIOS with a password...\\:D/ 

So somebody who wants to see your Stuff, needs to know YOUR BIOS password...

But then, do NOT forget your BIOS password!

But, even in such a case, there is a way to overcome that lock...

...in the end, they WILL find a way to see your stuff, in any way...:( 

_Word of Advice_:

Anything that is "Locked" can be "Unlocked"....:( 

... and it is a matter of "How much Time" is needed for somebody to Break-in your Ubuntu... 

So, all you can do is to "Slow them down" a little...:-k

---

### Post by kvorion on 2006-02-22
I have changed the root pass many times in my college pcs that have dual booted win xp and fedora core-3. Simply boot into single mode and change the pass. But then those were ill managed pcs where nobody knew the root pass, so technically I wasnt doing anything bad. But anyone with ill intentions can do anything he/she wants. We definitely need better security in computers that are publicly accessible.

---

### Post by patrick295767 on 2006-02-22
[QUOTE=dvarsam]Hello ALL !!!

Since I like Ubuntu so much (& learning at the same time), I will give you this nice Tutorial regarding the:


_How to change a User's or ROOT's Password before Booting_:

To Log in in your Ubuntu, simply use your "user name" (you gave during the installation) & the "password" (you specified at that time).


If you have Forgotten your User's "password":


There are two ways to go on this:

1. To Change your current User's Password:

    a. Restart Ubuntu in Recovery Mode (at the Boot Menu select your Kernel & 
        "Recovery Mode" which will get you to the Command Line (the bash Shell's $ 
         or # prompt).

    b. Type:

	passwd <username>

    c. Enter a NEW "password".

    d. Then Reboot (using "reboot") your Ubuntu & Log in with your "username" & 
        the NEW "password" you specified.

2. To Create a NEW User Account:

    a. Boot Ubuntu in Recovery Mode (at the Boot Menu select your Kernel & 
        "Recovery Mode" which will get you to the Command Line (the bash Shell's $ 
        or # prompt).

     b. Type:

	useradd -m new_user_name

     c. Type:

	passwd new_user_name 

     d. Enter the NEW User's Password twice.

     e. Then Reboot (using "reboot") your Ubuntu & Log in with your NEW 
         "username" & "password" you specified.

IF Ubuntu does NOT let you type ANY of the above commands & requests a ROOT Password, do the following:

    _Note_:
    By default, there is NO "root" Password in Ubuntu (the ROOT Password is NOT 
    set).
    Once you Set a ROOT Password in Ubuntu, it requires it when you are in the 
    "Recovery Mode".
    You can use an Ubuntu Install CD to Reset the ROOT Password.

1. Insert the Install CD & at the CD Boot Prompt, type:

	rescue

2. Follow the instructions & when you are in the "Terminal", type:

	passwd root

3. Enter the ROOT Password twice in there & Add a NEW User account with:

	adduser

4. Enter your NEW User info & when your finished, type:

	adduser your_new_user_name admin

    _Note_:
    This is performed so that the NEW User can access System Tools as ROOT.

5. Then remove your InstallCD, Reboot (using "reboot") your Ubuntu & Log in with 
    your NEW User account.[/QUOTE]
   
If I mess up with passwords, I usually use : 
Knoppix bootable CD & 
go into the /etc/shadow file ... 

There is also one possibility to act.

Greetz

---

