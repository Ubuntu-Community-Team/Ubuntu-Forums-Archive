---
title: "Ubuntu Vs. Kubuntu"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by jkarns on 2007-07-27
I am new to Ubuntu...Linux in general. I am very happy with my Ubuntu machine right now. Having a little bit of an issue recognizing my Belkin USB Wireless Adapter...but I'll post about that one later. I do IT support and consider myself very Windows savy...but this Linux experience admittedly has been frustrating. But, all in all...I'm diggin' it. I'll learn...

Here is my question. I am going to be buying or building my mom (65 years old and just finally has gotten comfortable with XP) a new machine. She uses it primarily for email, web browsing, pulling pics off her camera, and basic photo editing and printing. So, I think Ubuntu would be perfect for her. It'll keep her out of the spyware/adware/virus trouble that I have to clean up for her every 6 months.  Also considering if I get her a new Windows install...I'm going to have to teach her how to use Vista. Honestly, I would rather teach her Ubuntu rather than Vista. BUT, I have heard that maybe Kubuntu would be a better match. I have heard that it is a little more "Windows user" friendly. Does anyone have any opinion. Is Kubuntu a better match for someone who is barely XP literate? 

Can I dual boot Ubuntu/Kubuntu to see for myself...? OR just stick KDE on top of Ubuntu. Like I said...I am new...and not sure how this would go...

---

### Post by Hossie on 2007-07-27
KDE and Gnome are just a thing of personal "believe". You can install both of them and can choose which one to open when you want to log in.

---

### Post by LaRoza on 2007-07-27
> **jkarns said:**
> Does anyone have any opinion. Is Kubuntu a better match for someone who is barely XP literate? 

Can I dual boot Ubuntu/Kubuntu to see for myself...? OR just stick KDE on top of Ubuntu. Like I said...I am new...and not sure how this would go...
Install Ubuntu, then run this command in the terminal
```

sudo aptitude install kubuntu-desktop
```
Welcome, by the way!

You will be able to select which desktop environment you will use when you log on, but the apps will be usuable no matter what DE you use.

-EDIT This is "sticking KDE on top of Ubuntu", no need to dual boot.

---

### Post by Majorix on 2007-07-27
K Desktop Environment is said to be more eyecandy. I also heard about Windows users being more comfortable with it than they are with Gnome. But it is usually more matter of a taste than something certain. So it is upto you to decide.

Yes you can "dual boot" KDE and Gnome. It is not totally a dual boot, as they will both use the same partitions to write/read data. This is done by either

Doing this from Ubuntu:
```
sudo apt-get install kubuntu-desktop
```

Or this from Kubuntu:
```
sudo apt-get install ubuntu-desktop
```

Good luck!

---

### Post by LaRoza on 2007-07-27
I foresee confusion...

I used "sudo aptitude ...", someone else used "sudo apt-get", both do essentially the same thing, neither is better.

---

### Post by OldGrey on 2007-07-27
Hi. I suggest that you read the following, look under the "Playing Around" section on the LHS for Gome / KDE comparison and set up. Gnome is the Ubuntu Desktop and KDE the Kubuntu Desktop.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

By the way this is a useful resource for all sorts of Ubuntu FAQs.

---

### Post by dreadlord_chris on 2007-07-27
> **jkarns said:**
> I am new to Ubuntu...Linux in general. I am very happy with my Ubuntu machine right now. Having a little bit of an issue recognizing my Belkin USB Wireless Adapter...but I'll post about that one later. I do IT support and consider myself very Windows savy...but this Linux experience admittedly has been frustrating. But, all in all...I'm diggin' it. I'll learn...

Here is my question. I am going to be buying or building my mom (65 years old and just finally has gotten comfortable with XP) a new machine. She uses it primarily for email, web browsing, pulling pics off her camera, and basic photo editing and printing. So, I think Ubuntu would be perfect for her. It'll keep her out of the spyware/adware/virus trouble that I have to clean up for her every 6 months.  Also considering if I get her a new Windows install...I'm going to have to teach her how to use Vista. Honestly, I would rather teach her Ubuntu rather than Vista. BUT, I have heard that maybe Kubuntu would be a better match. I have heard that it is a little more "Windows user" friendly. Does anyone have any opinion. Is Kubuntu a better match for someone who is barely XP literate? 

Can I dual boot Ubuntu/Kubuntu to see for myself...? OR just stick KDE on top of Ubuntu. Like I said...I am new...and not sure how this would go...

You can install KDE alongside GNOME - then from the login screen Sessions menu you can choose which desktop to log into.
```

sudo apt-get install kubuntu-desktop

```

I prefer KDE myself - but honestly, from my experience, either one is a pretty easy transition from the XP desktop....

---

### Post by armandh on 2007-07-27
use the Ubuntu disk live to let mom test drive Ubuntu
it took only about 3 hrs for this window person to get Ubuntu in hand.
it took only about 3 hrs more to think Ubuntu is great possibly better.

I have a few programs and driver needs that keep me from abandoning the big W all together.

---

### Post by moore.bryan on 2007-07-27
*i agree completely with dreadlord_chris... you should install both and play-around.  i, too, have heard the ubuntu=mac, kubuntu=xp thing... most hardcore windows users i've turned-on to linux prefer kubuntu, but that's just anectdotal.*

---

### Post by rich.bradshaw on 2007-07-27
KDE is obviously technically better than GNOME in many ways, but people still prefer to use GNOME - in the end it's up to the end user.

Let her see both, let her choose.

Gnome has many options missing in order to make it easy for people to use.

KDE has millions of options everywhere (hence technically better), but for some people that's overwhelming and annoying.

The only reason people say KDE is more like windows is because theres 1 panel, at the bottom.

GNOME can be configured like this as well though, so that's a bit of a pointless argument...

---

### Post by Rui Pais on 2007-07-27
This is a duplicate of your one:
[http://ubuntuforums.org/showthread.php?t=511003](http://ubuntuforums.org/showthread.php?t=511003)

and a dup of at least a dozen by others on this subject...
Maybe mods should merge them.

---

### Post by frodon on 2007-07-27
duplicate threads merged

---

### Post by moore.bryan on 2007-07-27
> **rich.bradshaw said:**
> The only reason people say KDE is more like windows is because theres 1 panel, at the bottom.
*not meaning to offend any kubuntu-ers out there, but i think kde "acts" more like windows, at least as far as the interface is concerned.  when i showed my mom ubuntu and kubuntu, she commented on how much kubuntu "acted" like her windows.  she even asked if ubuntu was based on macs.  ;-)*

---

