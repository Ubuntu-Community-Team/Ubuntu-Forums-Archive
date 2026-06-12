---
title: "[SOLVED] Problem with Windows Live Hotmail on Firefox"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-10-12
My Hotmail opens fine with Firefox, except i get the "classic version" meaning the lite version of Live Hotmail. Never had this problem before!
any ideas? 
thanks:)

---

### Post by ramjet_1953 on 2007-10-12
Isn't there a link when you open the Classic Version to change to the Live version?

I seem to remember doing this a while ago and just clicked on a link which I think may have been near the top right of the screen.

Regards,
Roger :cool:

---

### Post by Tom Mann on 2007-10-12
The lite version is so as although Windows Live Hotmail supports Firefox in Windows, has never done in Linux AFAIK. Coincidence?

---

### Post by Mazen on 2007-10-12
The lite version is different from the classic version.
I already have Live,but don't have all the functions in it,like drag and drop and the right-click and so on.
The thing is it says i should have IE 5 or more, or Firefox 1.5, in windows it works, and always did in Ubuntu but not after my Gusty upgrade!

---

### Post by Mazen on 2007-10-12
any one??!!

---

### Post by dmizer on 2007-10-13
hotmail is owned and operated by microsoft.  don't expect to get this working 100% in firefox/linux.  hotmail live is also very new and it still going through many changes.  it's also linked to the windows operating system through internet explorer, which of course is not possible through firefox.

my advice to you would be to configure thunderbird to download your hotmail and only use hotmail for email alone.  then sign up for a gmail account and use gmail for your live services as it's more friendly to firefox, and far less invasive.

---

### Post by Mazen on 2007-10-13
> **dmizer said:**
> hotmail is owned and operated by microsoft.  don't expect to get this working 100% in firefox/linux.  hotmail live is also very new and it still going through many changes.  it's also linked to the windows operating system through internet explorer, which of course is not possible through firefox.

my advice to you would be to configure thunderbird to download your hotmail and only use hotmail for email alone.  then sign up for a gmail account and use gmail for your live services as it's more friendly to firefox, and far less invasive.
Thanks for the advice, i've had a hotmail account for ages, and also had a gmail account when gmail was still testing.
The only reason i posted this was because i've been using Windows Live Hotmail with Ubuntu ever since it started, and this is the first time this happens.
I have Evolution configured to get both my gmail and my hotmail, that is not an issue the only thing is the web based inbox is not in its full functioning mode.
Thank you anyways

---

### Post by dmizer on 2007-10-13
yeah ... i don't actually know what the real problem is here.  on some of my computers, it works ... some it doesn't (windows or linux or otherwise).  not sure why.  but again, hotmail live is going through changes frequently so my gut reaction is that this is not a linux/firefox problem, but with the hotmail interface.

---

### Post by Zurd on 2007-10-19
My friend has the same problem, I don't since I'm using Yahoo Mail Beta which is very nice. But we look into this problem and found the problem. Type about:config in a new URL and search for general.useragent.vendor and switch it from Ubuntu to Firefox and Windows Live Hotmail will work, don't restart your browser.

We can confirm this on Ubuntu Gutsy 7.10, we don't know why but it worked perfectly well with Ubuntu Feisty 7.04.

The last problem is to actually make this switch eternally because if you restart firefox, it'll switch back from Firefox to Ubuntu and you'll have to make the changes again.

---

### Post by Mazen on 2007-10-19
> **Zurd said:**
> My friend has the same problem, I don't since I'm using Yahoo Mail Beta which is very nice. But we look into this problem and found the problem. Type about:config in a new URL and search for general.useragent.vendor and switch it from Ubuntu to Firefox and Windows Live Hotmail will work, don't restart your browser.

We can confirm this on Ubuntu Gutsy 7.10, we don't know why but it worked perfectly well with Ubuntu Feisty 7.04.

The last problem is to actually make this switch eternally because if you restart firefox, it'll switch back from Firefox to Ubuntu and you'll have to make the changes again.
PERFECT!!!
I thank you very much!
Now if there's a way to put this thread as SOLVED so other people can benifit from it!

---

### Post by Dr Small on 2007-10-19
> **Mazen said:**
> PERFECT!!!
I thank you very much!
Now if there's a way to put this thread as SOLVED so other people can benifit from it!
Thread Tools > Mark as Solved

---

### Post by Mazen on 2007-10-19
For me it worked even after restarting Firefox!
Anyways does it work like this?i mean is putting the thread as solved good?!?i never did that before!
Thanks anyways for the help guys

---

### Post by Sirron on 2007-10-24
I think this should be bug reported. It was stopping both the full version of Hotmail and Live.com working. And, isn't there that rule about not overly branding things to make life easier for people making ubuntu derived distros?

Who's with me?

---

### Post by AngryAnimal on 2007-10-25
Guys

Just installed 7.10 and foun your thread

Some stuff I think might help, not sure if this the offical way but it seems to be working for me.  The setting seems to remain after shutdown/restart.

got to terminal and type
sudo gedit

enter root password and then when gedit starts find the file 

/etc/firefox/pref/firefox.js


the file looks something like
************************************************************************************

// This is the Debian specific preferences file for Mozilla Firefox
// You can make any change in here, it is the purpose of this file.
// You can, with this file and all files present in the
// /etc/firefox/pref directory, override any preference that is
// present in /usr/lib/firefox/defaults/pref directory.
// While your changes will be kept on upgrade if you modify files in
// /etc/firefox/pref, please note that they won't be kept if you
// do them in /usr/lib/firefox/defaults/pref.

pref("extensions.update.enabled", true);

// Use LANG environment variable to choose locale
pref("intl.locale.matchOS", true);

// Disable default browser checking.
pref("browser.shell.checkDefaultBrowser", false);

*************************************************************************************

add a new line to the bottom like this

// To default make hotmail work
pref("general.useragent.vendor", Firefox);

save/close the file and then retry Firefox

---

### Post by AngryAnimal on 2007-10-25
please ignore my entry!  Its somewhere like this but I can't find it (yet)

---

### Post by bidaoui on 2007-10-30
> **Zurd said:**
> My friend has the same problem, I don't since I'm using Yahoo Mail Beta which is very nice. But we look into this problem and found the problem. Type about:config in a new URL and search for general.useragent.vendor and switch it from Ubuntu to Firefox and Windows Live Hotmail will work, don't restart your browser.

We can confirm this on Ubuntu Gutsy 7.10, we don't know why but it worked perfectly well with Ubuntu Feisty 7.04.

The last problem is to actually make this switch eternally because if you restart firefox, it'll switch back from Firefox to Ubuntu and you'll have to make the changes again.

I had to reinstall Ubuntu on my computer and I face the same trouble, not being able to check my emails on Hotmail (connection reinitialized before i can even see any log in page). I tried the above solution but it didn't work. Could anyone help me ? I remember I had the same trouble when I first turned form windows to Ubuntu but I can't find the solution I used...

---

### Post by Mazen on 2007-10-30
> **bidaoui said:**
> I had to reinstall Ubuntu on my computer and I face the same trouble, not being able to check my emails on Hotmail (connection reinitialized before i can even see any log in page). I tried the above solution but it didn't work. Could anyone help me ? I remember I had the same trouble when I first turned form windows to Ubuntu but I can't find the solution I used...
I don't think that your issue is the same as the one mentioned above.
Yours would probably relate to your internet connection or the settings you have in firefox.
Have you tried it with Opera or another browser?
And as for the issue above, it worked almost all the time for me, i mean i don't have to redo the whole thing every time i open firefox, but sometimes it works some other times no, and when it doesn't refreshing or restarting firefox would do the job!

---

### Post by bidaoui on 2007-10-30
I tried with Epiphany and I have the same problem as with Firefox, but only with Hotmail. My connection is perfectly working as i can log in here and use it for other websites without a single problem. Thus, I can't get logged on MSN through pidgin, which works perfectly for jabber...

I've been looking for a solution since this morning, with no success...

---

### Post by Mazen on 2007-10-30
so apparently it's not a Firefox issue, it's a "Microsoft" issue!
try other computers on your internet connection if possible, i don't have much information about the ports and all that, but i guess that would be the problem and not Firefox or any browser.
Sorry i'm not much help but as soon as i can figure it out i'll post something, hope some of the guys here can help you.
Peace!

---

### Post by bidaoui on 2007-10-30
Thanks for your help and concern Mazen :)

I try to figure out some solutions (maybe the timeout length in the connection in Firefox parameters: I tried but still no result.. Maybe is it related to my router or the connection configuration though I didn't change a thing whe I reinstalled Ubuntu... I don't know...)

If anyone has some new idea, I'd really appreciate as my hotmail address is not only for fun purpose... :(

[Edit] It doesn't seem to be a hotmail troubel as people around seem to have a good connection with windows running PC...

---

### Post by andrewisett on 2007-10-30
Worked for me as well.. I have been impressed with the Windows Live Functionality, and going back to the Basic version was crippling.

---

### Post by bidaoui on 2007-10-31
I just wanted to inform you that I eventually came to a soution; changing MTU from 1500 to 1412.

---

### Post by fragos on 2008-01-30
Many times this kind of issue is caused by a lack of web master knowledge.  They make assumptions based on whatever information they retrieved about the browser or flash version you are using that are incorrect.  With the exception of sites using Active-X instead of JavaScript the problem is that the web master has incorrectly determined your browser isn't compatible.  Fortunately most sites, like Google, don't use Microsoft proprietary stuff.

---

