---
title: "login as root"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-11-07
how do you login automatically login as root in 7.10?
Thanks

---

### Post by rsambuca on 2007-11-07
Although not recommended, you can activate the root login in Ubuntu.  Details on how to do so can be found near the[ bottom of this page]("https://help.ubuntu.com/community/RootSudo"), however, I recommend you read the entire page to see why it isn't recommended.

---

### Post by finer recliner on 2007-11-07
$sudo su

or 

$sudo -i


again, as mentioned above, ubuntu worked hard to make root unnessary. stick to just sudo. much safer.

---

### Post by endlessurf on 2007-11-07
would love to but the computer is in my car and i only have a touch screen.  I think it would be best if i did not have to try to type in my password while cruzing down the freeway at 80mph

---

### Post by endlessurf on 2007-11-07
ii need root abilities because of a program i have to calibrate the screen and a couple of other problem areas i run into

---

### Post by rsambuca on 2007-11-07
Personally I think it is nothing more than irresponsible negligence to use a computer while driving.

---

### Post by endlessurf on 2007-11-07
it has gps and my complete music selection on it all at a touch running myth tv.  at least i won't ever have to reach into the back seat to grab my cd case again

---

### Post by Tekno_Cowboy on 2007-11-07
> **rsambuca said:**
> Personally I think it is nothing more than irresponsible negligence to use a computer while driving.

I wholeheartedly agree. Why on earth do you need to use your computer while driving?

edit:I guess you answered it already. Have you considered voice commands?

---

### Post by endlessurf on 2007-11-07
wold not be a bad idea, but setting up the touchscreen was about the limit of my computer skills. voice commands might be way to much for me because it would have to deal with my music and cell phone

---

### Post by endlessurf on 2007-11-07
plus I have mythtv, workspaces, and touch screen set up so you can't get at a command line or even a taskbar without a keyboard.

---

### Post by rsambuca on 2007-11-07
I can't bear this anymore.  You are a disaster waiting to happen.  In many jurisdictions it is actually illegal to be using cell phones and/or computers while driving.

---

### Post by Tekno_Cowboy on 2007-11-07
> **rsambuca said:**
> I can't bear this anymore.  You are a disaster waiting to happen.  In many jurisdictions it is actually illegal to be using cell phones and/or computers while driving.

I know it is here in Minnesota. Except the Police. I wonder how that works out?

---

### Post by bluenova on 2007-11-07
> **rsambuca said:**
> I can't bear this anymore.  You are a disaster waiting to happen.  In many jurisdictions it is actually illegal to be using cell phones and/or computers while driving.

I suppose you pull over to change the radio station or adjust the temperature? I don't see the difference between that and using MythTV.

---

### Post by Arthur Archnix on 2007-11-07
You can also create a new group, called awth, add yourself to that group, and give auth administrator rights to the programs you plan on using. It's not too hard. Search for how-tos on editing the sudoers file. There was a real good one over on the debian foruns not long ago. Oh and the most important thing is that awth wouldn't have to enter the password to run sudo once logged in. If you set that up with auto-login you have something similar to loggin in as root, probably about as secure, but at least twice as cool.

---

### Post by dcstar on 2007-11-07
> **bluenova said:**
> I suppose you pull over to change the radio station or adjust the temperature? I don't see the difference between that and using MythTV.

Yep, no need to watch the road when there is "TV" distracting a driver............ :confused:

---

### Post by hyper_ch on 2007-11-07
On that whole logging in as root thing I tend to think that if you have to ask how to login as root then you are not ready yet to login as root ;)

---

### Post by endlessurf on 2007-11-07
Arthur Archnix - thanks for the reply, I'll take a look at the process you mention, but i have a feeling it will fall short when it comes to the calibration program.  


> In many jurisdictions it is actually illegal to be using cell phones and/or computers while driving

I suppose you are busting people in higher end cars who have a computer in their car that does the same as mine.  I also suspect you are busting people using tom tom and people who have an Ipod hooked up to their car

> On that whole logging in as root thing I tend to think that if you have to ask how to login as root then you are not ready yet to login as root 


I can login as root no problem, my only problem is I want to ditch the keyboard.  

I'm more interested in starting up the computer and have it login as root without using the keyboard or questioning me if i really want to sign on as root.  That is what I am looking to find out.

or

have some sort of start up script that will run sudo su and not ask for my password or autofill 

The idea is to get rid of the keyboard and mouse and to beable to run sudo commands.

---

