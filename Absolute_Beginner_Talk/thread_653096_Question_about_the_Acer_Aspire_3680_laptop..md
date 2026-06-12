---
title: "Question about the Acer Aspire 3680 laptop."
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by freexzai on 2007-12-29
I checked the forums and saw a few unresolved issues with this laptop. I am trying to get my GF to switch to Ubuntu and shes very receptive but I don't want to be playing constant tech support. 

I see a few threads about weird sound issues. Headphones needing to be played with to make it work and when you switch back to the onboard sound you have to change something back. Is this a huge weird problem and can I get an answer about what exactly needs to be changed to go back and forth?

Also the problem with the Atheros onboard wifi. Some people seem to have a lot of problems getting wifi to work and continue working. 

Any answers will be greatly appreciated.

Thank you.

---

### Post by Nem1976 on 2007-12-29
l'm not sure about the Aspire series but I'm running gutsy on a Acer Travelmate 4200 and currently have no problems.  Wireless worked right after install as well as the headset port works with out any configuration changes needed.  I'm playing my music with amarok as well.  

This is the first laptop I install ubuntu on and I'm very pleased.  I have it on my work desktop but just finished the install on my laptop and it's working great.  I have Compiz and AWN installed as well no issues.

---

### Post by geekcrossing on 2007-12-30
I have a Acer Aspire 3680 laptop. I had Ubuntu installed as dual boot with Vista. I can not get wifi to connect. The laptop has a physical switch on the front to turn wireless on or off.
I am fully prepared to take the plunge (wipe Vista and just use Ubuntu) if I can get the wireless to work. 

The laptop speakers do not work but the headphone jacks so that is something I can live with. I have to have wireless access so some one please help me. I can't take Vista anymore! My first computer a 300 mhz HP with Win 98 was better than Vista!

---

### Post by jken146 on 2007-12-30
I have an Aspire 3503 (borrowed actually) and I can't say I like it much.  Not that that's relevant.  The wifi didn't work straight away (it's an Atheros chipset, can't tell which one now 'cause I'm in a newish Arch install and haven't bothered to sort it out yet).  Madwifi did the trick -- very little hassle.

---

### Post by PriceChild on 2007-12-30
I have an aspire 5600.

I noticed that I need to ensure the wireless switch is turned on *before* the main part to the ubuntu boot. If I turn it off or on later things just don't work.

---

### Post by bbqsandwich on 2008-01-08
I have an Acer Aspire 3680 laptop. I got the wireless working using these instructions:

[http://ubuntuforums.org/showthread.php?t=512828&highlight=ar5007eg](http://ubuntuforums.org/showthread.php?t=512828&highlight=ar5007eg)

However, I had to make a minor change. The command in Step 1 automatically downloads ndiswrapper 1.5 (as of yesterday, Jan. 7, 2008...). You will need 1.51. If you try the steps with 1.5, you will likely get errors (at least I did) installing ndiswrapper and when you go to perform Step 6 in the instructions linked above, it will say there is no ndiswrapper.

So, to get 1.51, when you enter the above command, it will download 1.5, but check the terminal for the full path of the ndiswrapper download that it gets. I don't remember exactly what it was, but it is something like

[FONT="Courier New"]wget [http://xxxxxx...ndiswrapper-1.5.tar.gz](http://xxxxxx...ndiswrapper-1.5.tar.gz)[/FONT]

Simply copy that line, paste it into your terminal again but add a "1" after the 5 to get the newer version. Then use the instructions in the first link above, but the command in step 2

[FONT="Courier New"]tar xvf ndiswrapper-newest.tar.gz[/FONT]

will actually be

[FONT="Courier New"]tar xvf ndiswrapper-1.51.tar.gz[/FONT]

Everything else should be the same.

I hope that helps! I am, however, still very much a new Ubuntu learner, so if there are others here who see errors in my instructions, please correct me. They did work for me, though, and I am happily on the Internet, wireless, with my Aspire 3680.

Regarding your other thoughts, I do not have sound problems. However, I have the same suspend/hibernate freeze problem that others on these forums have reported. Even with that problem, Ubuntu is still more stable and usable than Windows Vista. ;-)

---

### Post by Turtle.net on 2008-06-24
> **PriceChild said:**
> I have an aspire 5600.

I noticed that I need to ensure the wireless switch is turned on *before* the main part to the ubuntu boot. If I turn it off or on later things just don't work.

I also have an Aspire 5600 and the wireless is not working on a fresh install of 8.04.

How do you know if the switch is on or not, i tried several time with no luck so far ...

Extract of ```
 $ sudo cat /var/log/messages | grep switch
 Kill switch must be turned off for wireless networking to work.

```

---

