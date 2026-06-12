---
title: "[SOLVED] Firefox in linux vs firefox in windows"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-11-28
This is driving me bonkers! I am a long time (is two years a long time?) Firefox in windows user. I long ago learned that there are one or two sites that I have to open in IE because of something called activeX that I really don't understand but whatever... Anyway now that I am basking in the glory that is Ubuntu I have come across several sites that I use on a regular basis that don't completely work in Firefox when I am booted into Ubuntu but that work just fine in Firefox when I am in windows. What is the deal and what do I need to do to avoid booting into windows as much possible?:)

---

### Post by samuel.rajesh on 2007-11-28
> **boriquajake said:**
> This is driving me bonkers! I am a long time (is two years a long time?) Firefox in windows user. I long ago learned that there are one or two sites that I have to open in IE because of something called activeX that I really don't understand but whatever... Anyway now that I am basking in the glory that is Ubuntu I have come across several sites that I use on a regular basis that don't completely work in Firefox when I am booted into Ubuntu but that work just fine in Firefox when I am in windows. What is the deal and what do I need to do to avoid booting into windows as much possible?:)

Might be flash  ,install restricted software and u should be fine

---

### Post by philinux on 2007-11-28
Have you got java installed and flash etc.

What are the sites in question maybe we can test them out.

---

### Post by boriquajake on 2007-11-28
The main site I need to access today is [www.dishnetwork.com](www.dishnetwork.com). I am a Dish Network retailer and I need to be able to access the site to help customers and look up information. The first time I tried to access it I got the little notice saying I needed to download some plugins. It gave me the option of installing one that looked like it was open source and one that was actually flash. In the spirit of OSS I installed the free-looking one and found that it didn't seem to help so I tried again and installed the other. In both cases the site still looks odd and is missing a lot of functionality. For example there are no fields next to where it asks for username and password so I can't log in.

---

### Post by boriquajake on 2007-11-28
I thought it might have something to do with either Flash or Java but because I am not sure what either one of them are nor what they do I didn't mention that. ;-)

---

### Post by lespaul_rentals on 2007-11-28
Flash is the plugin your browser uses to display those flashy movies and graphics you see all over the web.  Java is the plugin your browser uses to run some web-based applications as well as other programs coded in Java.

Try running the following command in Terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Also, I despise Firefox in Linux (well, I actually despise Firefox in Windows too, but that's beside the point).  That's just my personal opinion, though.  I use Opera, you might want to try it out if you continue to experience problems.  If you are using Gnome, you might also try Epiphany.

---

### Post by timcredible on 2007-11-28
that site works fine with firefox on linux.  if you're using 7.10, it should ask you to download flash.  if not, take a quick look at the [ubuntu guide]("http://ubuntuguide.org") and see how to install flash.

---

### Post by philinux on 2007-11-28
you've not got flashblck plugin installed I hope.

other than that its the plugin flash non free you need.

---

### Post by gn2 on 2007-11-28
As has been mentioned you need to install the restricted extras, there are three ways, through Add/Remove, through Synaptic Package Manager, or by opening a terminal and copying and pasting the following line of text:

sudo apt-get install ubuntu-restricted-extras

Press Enter then your password when prompted, and Enter again.
The required software will be downloaded and installed for you.
You will have to accept licences during the process.

You will now be able to use that site.
Disabling AdBlock Plus helps on that site (if you use this add-on)

---

### Post by fineas on 2007-11-28
If you still find useful web pages that can be displayed only on Internet explorer, try this: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Install_Internet_Explorer_6_for_Wine](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Install_Internet_Explorer_6_for_Wine)
Notes:1) Active-X is very often responsible for installing and executing malicious commands.You should chek about that. 2) [http://www.dishnetwork.com](http://www.dishnetwork.com) is showed just fine to my firefox browser.

---

### Post by boriquajake on 2007-11-28
Thank you all very much. It worked perfectly.

---

### Post by ceduriki on 2007-11-28
Yeah, firefox is pretty much the same on all platforms. If you get lal the plugins from the add/remove programs list, you'll be good to go.

---

