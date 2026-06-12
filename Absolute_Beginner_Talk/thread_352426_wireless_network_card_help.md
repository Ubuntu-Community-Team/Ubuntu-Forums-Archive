---
title: "wireless network card help"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Timmy66 on 2007-02-03
I have a trendnet TEW-423 PI wireless network card.How can I get it installed on my Ubuntu Edgy.

---

### Post by crispy_420 on 2007-02-03
Just a quick google search but it looks like you may have to use non-native linux driver (read ndiswrapper). So it looks like you may have no choice but use a non-linux driver. Just from what I've read it has a Texas Instruments chipset.

But there is a chance yet, just found this: [acx111 driver]("http://acx100.sourceforge.net/"). I have not tried it but it looks like a reversed engineered driver, so good luck.

And as a favor to others, chime in on any luck you had or didn't.

---

### Post by jml on 2007-02-03
To be frank, getting wireless working is a real challenge, even for Linux guru's, (which I am not.)  If you still have problems, you might want to ask your question on the Networking/wireless sub-forum.  You might find someone who can help there as well.  And I agree with the previous post.  You may have to rely on ndiswrapper and the Windows driver for your card.  Good luck.

Joe

---

### Post by crispy_420 on 2007-02-05
Try the driver I mentioned and try to install network manager. If the driver installs fine and recognized by the OS, network-manager will simpify your life on the go.

And by the way, I thought wireless was easy to setup in linux than windows. I could even get signals that windows comps could not get. Maybe it was just my laptop.

---

### Post by akajonesy on 2007-02-05
If you have the live disc or a wire connection install the restricted modules and reboot (use synaptic and search for restricted-modules). It worked for me. (no clue at all what it fixed, but didn't have to use ndiswrapper which I couldnt get to work).

---

### Post by akajonesy on 2007-02-05
> **crispy_420 said:**
> 
And by the way, I thought wireless was easy to setup in linux than windows. I could even get signals that windows comps could not get. Maybe it was just my laptop.

It's one of those things that it works easy or it's hell to set up. I've had one of each. I think it's a bit unfair on linux though since there seems to be a mindset that if "it worked on windows it should work on linux", rather than people remembering that it's a different OS so hardware compatibility should be considered at the outset.

---

### Post by crispy_420 on 2007-02-06
I know driver support will be an issue when I purchase a laptop next time.

I don't know you guys financial situations (dropping around $40) or level of hardware knowledge (taking apart a laptop), but wouldn't it be easier to just get a different wifi card and replace the offending one. If that is an option, I would suggest one of two chipsets: Intel or atheros. I have an atheros based one, no trouble here. It replaced a ralink (rt2500). And I have heard lots of good about intel. Just an idea.

---

### Post by jonnyburns on 2007-02-06
try to google some driver's for the model... that is what i have to do everytime i buy a new piece of hardware for my ipaq, kinda fun though, like a hunt for the right non-native driver if you will

---

### Post by seth556 on 2007-02-11
I used the ndiswrapper command stuff and installed my TEW-423pi card very easily, no problems. I'm very happy about this.

---

### Post by u-blunt-2 on 2007-04-27
Seth, what distro did you install it on ?
I want to upgrade to amd64, but the only thing holding me back is my darned tew-423pi wireless card. The TrendNet website does not have 64 drivers, but I recently noticed they have a Vista HowTo for this card. 
Anyone try installing on 64 bit ?

---

### Post by u-blunt-2 on 2008-01-14
bump
**ATTN AMD64 users **

---

### Post by kdnewton on 2008-01-14
I can't understand how some people are getting it to work so easily. I tried installing with ndiswrapper last night on Ubuntu 7.10 (gutsy trendnet tew 423 PI, for keyword purposes).

I tried installing the WINXP and the WIN2000 drivers via ndiswrapper and still no luck.

lspci would show the realtek wireless. I've got a revision C wireless card.
iwconfig and ifconfig would both show wlan0
From the CLI I'd try "iwlist wlan0 scan" and it would come up with no results even though I was right next to my router and another computer was connected via wireless.

I b0rked it up enough last night I'm going to reinstall 7.10 again and try over from scratch. Good luck getting your trendnet tew-423 working. With any luck someone will post a guideline of what they did to get it to work.

---

