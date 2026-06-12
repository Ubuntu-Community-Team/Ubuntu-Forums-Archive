---
title: "Is Ubuntu something Bill Gates dreamed up to put us off Linux??"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by Ankton on 2006-08-27
I have had nothing but problems installing Ubuntu 6.06 LTS.
First of all, I am installing it onto an IBM eserver xseries 300. This same server had an install of Debian running on it no probs.
I have had no end of trouble trying to get the integrated network controller card detected and yes it is in the supported hardware list /sigh. I have even put in half a dozen other NIC's into the pci slots but to no avail.

Now I am not one to let something like this get to me so i decided to install without the NIC's being detected and sort it out later via the CLI. Low and behold when I finally get to the login prompt after getting throught the install without the NIC's being detected, my keyboard decides it doesnt want to work!!! I have just been using it to go through all the steps on the install WHY IS IT NOT WORKING!!!!! I have changed to other keyboards still no luck. GIVE ME A BREAK!!!!! They are PS2 keyboards btw... can anyone shed some light as to what is going on here PLEASE.

---

### Post by GuitarHero on 2006-08-27
People are less likely to help you when you post with an attitude.  We understand your frustration, we've all have had it before.  Also this in no way sounds like an absolute beginner talk worthy problem, a little more advanced don't you think?    Have youm tried using a usb keyboard?

---

### Post by az on 2006-08-27
> **Ankton said:**
> I have had nothing but problems installing Ubuntu 6.06 LTS.
First of all, I am installing it onto an IBM eserver xseries 300. This same server had an install of Debian running on it no probs.


Try the live cd to see if your keyboard works.  The server kernel sometimes does not play nice with some keyboards and mice.  

What kind of NIC is it?

And those are two bugs, BTW.  It is not designed to be that way, you know.

---

### Post by Ankton on 2006-08-27
Granted, I am frustrated and yea sorry bout the attitude ill clamp it up right now... X ....done.

In response to your this is not a beginners thing... this is the first time i have ever installed a Linux operating system and the first time I have ever been on a Linux forum so I am sort of a beginner :) I have in the past done some unix stuff so i know a little about the CLI. If you could be so kind as to point me in the right forum direction ill be happy to rephrase my "frustration" there. Respectfully.

---

### Post by Ankton on 2006-08-27
My Nic is Intel i915G chipset (ethernet integrated) and ill give a usb keyboard a try as u suggested ty.[-o<

---

### Post by blackened on 2006-08-27
> First of all, I am installing it onto an IBM eserver xseries 300. This same server had an install of Debian running on it no probs.

If it ran perfectly on Debian, then why switch to Ubuntu?

---

### Post by user1397 on 2006-08-27
> **blackened said:**
> If it ran perfectly on Debian, then why switch to Ubuntu?there is quite a bit of irony in this post....the very fact that an ubuntu user would say such a thing is a paradox :p

why do you think all of us here switched to ubuntu???:D

---

### Post by Emerzen on 2006-08-28
The above post was the best place to start...does a live CD of Dapper boot up properly?

---

### Post by aysiu on 2006-08-28
> **erik1397 said:**
> there is quite a bit of irony in this post....the very fact that an ubuntu user would say such a thing is a paradox :p

why do you think all of us here switched to ubuntu???:D
I don't see why that's a paradox. Maybe people switched to Ubuntu because Debian *didn't* work perfectly for them.

The question is why switch to Ubuntu if Debian *does* work perfectly.

---

### Post by Ankton on 2006-08-28
> If it ran perfectly on Debian, then why switch to Ubuntu?


I was told to.:?

---

### Post by bodhi.zazen on 2006-08-28
> **erik1397 said:**
> there is quite a bit of irony in this post....the very fact that an ubuntu user would say such a thing is a paradox :p

why do you think all of us here switched to ubuntu???:D

I second that. In the end the distro is not as important as hardware recognition.

Why not stay with what works, Debian is a fine distro and as a server may be preferable to Ubuntu.

---

### Post by Ankton on 2006-08-28
Ok for some reason the USB keyboard doesnt work but i plugged the ps2 keyboard back in and booted up and now it works...which brings me to another problem... when i go to use sudo <insert command here> it asks me for a password but i didnt get any opportunity to give the su a password in the install phase. What do i do now? How do i run things as su?

---

### Post by Shadyman on 2006-08-28
Perhaps the PS2 was partially unplugged. It happens sometimes, even on my desktop. The scary part is that my keyboard doesn't move.

From one UNIX person to another, there are a few differences with Ubuntu... Let's call them "safety measures" or "PEBCAK-resistant features" ;)

"sudo" is a command replacement for SU, it 'do'es one command instead of logging you in as root, etc. So by default, the SU password is a randomly-hashed long (can't remember how long) password. There are instructions on how to circumvent the "root lockout" at []("http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password"). Again, this is a security measure to prevent attacks such as "User Priviledge Elevation", or in english, the "look, you're root, now I'm root". If you run normally as a user-level user, anyone who is able to compromise your system can only access user-level features. 

On a separate note, with root disabled, any attacker would have to know your username as well as password, instead of just using 'root' as the username, and brute-forcing the password, or however they would do it.

The choice is yours, and if you were "told" to use Ubuntu, I would bring the decision up with him or her (or them) about the setup of su vs sudo, and which one he, she, they or you like best.

Cheers!

---

### Post by Shadyman on 2006-08-28
I vote for moving this thread to the "Other Support Options > Server Talk" forum :razz:

---

### Post by hwroth1 on 2006-08-28
I am a newbie myself so don't expect anything smart.

When I used the 686 kernal of ubuntu my keyboard and mouse would not work.

when I switched to the 386 kernal it worked fine.If you are using the 686 maybe a switch would help. 

Part of the reason I am working with linux is to learn how to use it. 

The trials and tribulations are part of the fun. I don't know if I would use it as my only machine fortunatly I have others on my home network. 



hwroth1

---

### Post by steve.horsley on 2006-08-28
The password that sudo is asking for is your user password - the one that you just logged in with -  not the root password. In Ubunbtu, the root account is locked out so root cannot log in directly. You log in as a normal user, and then use sudo to borrow root priv whenever needed.

---

### Post by Ankton on 2006-08-28
thankyou that explains alot:)

---

### Post by toasted on 2006-08-28
Some good reading :o 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by user1397 on 2006-08-28
> **aysiu said:**
> I don't see why that's a paradox. Maybe people switched to Ubuntu because Debian *didn't* work perfectly for them.

The question is why switch to Ubuntu if Debian *does* work perfectly.I meant that obviously most people switched to ubuntu because they learned of its greatness, so why not switch to ubuntu from debian if you know that it will out-do debian in many (but not all) ways?  (of course, this wasn't the case for this exact situation, so i'll just stop blabbering about...)

---

### Post by Klaidas on 2006-08-28
What has Windows and Bill got to do with it?

---

