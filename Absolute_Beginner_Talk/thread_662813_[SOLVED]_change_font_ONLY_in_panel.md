---
title: "[SOLVED] change font ONLY in panel?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2008-01-09
i want to change the FONT, not the color.  i know you can change the application font and it'll change it, but i want the panel font and the application font to be different...

---

### Post by FuturePilot on 2008-01-09
There's a little tool called Gnome Color Chooser that can do this. However it's not in the repos.
However there is a deb floating around out there
[http://3v1n0.tuxfamily.org/apt-repository/pool/edgy/3v1n0/gnome-color-chooser_0.1.3-3v1ubuntu0_i386.deb]("http://3v1n0.tuxfamily.org/apt-repository/pool/edgy/3v1n0/gnome-color-chooser_0.1.3-3v1ubuntu0_i386.deb")
:)

---

### Post by Niniel on 2008-01-09
I don't think Color Chooser changes fonts though.

Btw, a newer, and sadly the last, version can be found _here_. That's version 0.2.3.1.

---

### Post by Niklas Schröder on 2008-01-09
ah.  i actually have had that program for 5 months but didn't realize it could change the font.  ^_^;  

would someone mind telling me what the default "Application" font is in ubuntu?  i chose a different one, didn't like it, and am now trying to change it back but can't figure out which one it was...

---

### Post by FuturePilot on 2008-01-09
> **Niniel said:**
> I don't think Color Chooser changes fonts though.
It can. See screenshot.
> **Niklas Schröder said:**
> ah.  i actually have had that program for 5 months but didn't realize it could change the font.  ^_^;  

would someone mind telling me what the default "Application" font is in ubuntu?  i chose a different one, didn't like it, and am now trying to change it back but can't figure out which one it was...
Sans 
Size: 10

---

### Post by Niniel on 2008-01-09
I stand corrected. Thank you. :)

---

### Post by Niklas Schröder on 2008-01-09
you sure it's Sans?  stuff is blurry that didn't used to be...  which font would you suggest?

---

### Post by FuturePilot on 2008-01-09
> **Niklas Schröder said:**
> you sure it's Sans?  stuff is blurry that didn't used to be...  which font would you suggest?

I'm sure. I haven't touched the fonts since I installed Gutsy. Blurry? Did you turn on the Subpixel rendering under System>Appearance>Fonts?

---

### Post by Niklas Schröder on 2008-01-09
yeah.  it's on.  everything looks a little different though...

[http://paperclipsandscrambledeggs.googlepages.com/Screenshot.png](http://paperclipsandscrambledeggs.googlepages.com/Screenshot.png)

---

### Post by JackTheDipper on 2008-01-09
> **Niniel said:**
> Btw, a newer, and sadly the last, version can be found [here]("http://ppa.launchpad.net/misery/ubun...color-chooser/"). That's version 0.2.3.1.

Hi, Niniel,
why do you think that 0.2.3 (i never released a 0.2.3.1 btw *g*) will be the last version of gnome-color-chooser? That's not true ;-)

---

### Post by Niniel on 2008-01-09
I said that because all the official links to the software were dead without explanation, so it looked like the project had been abandoned. I found a .deb file later at the link that I posted.

But if you really are the developer of this neat tool, and plan to keep/resume working on it, that would be fantastic.

---

### Post by JackTheDipper on 2008-01-10
> **Niniel said:**
> I said that because all the official links to the software were dead without explanation, so it looked like the project had been abandoned. I found a .deb file later at the link that I posted.

But if you really are the developer of this neat tool, and plan to keep/resume working on it, that would be fantastic.

I am ;-) and sorry, i had some trouble with domain and webserver, but the URL mentioned in the aboutdialog of gnomecc is working again since some months ;-)
Additionally there is a sourceforge.net project now ( [http://sourceforge.net/projects/gnomecc/](http://sourceforge.net/projects/gnomecc/) ) that allows to download latest versions and access the subversion repository.

Does anyone btw uses the compact profile that ships with 0.2.3? So many people complained about GNOME being too clumsy, but i got no feedback yet about this new little helper. ;-)

best regards,
Jack ;-)


[edit]
the next ubuntu version will btw most probably ship with gnome-color-chooser included.
[/edit]

---

### Post by Niniel on 2008-01-10
Compact profile?

I was looking for a way to change the colour of the text of my panels, that's when I discovered your tool. Haven't done much beyond that with it, so all I can say is that it worked great for what I needed done. 

Good to hear that your tool may be included with the next official release. Anybody who's new to the OS will be grateful for that. Thanks also for providing a new download link.

---

### Post by Niklas Schröder on 2008-01-10
not to ruin the conversation, but blurry fonts are still bugging the heck out of me.  are there any ideas?

---

### Post by JackTheDipper on 2008-01-10
> **Niklas Schröder said:**
> not to ruin the conversation, but blurry fonts are still bugging the heck out of me.  are there any ideas?

the "no unread mail" text doesn't seem to be blurred here.. looks very normal.
The text above seems to be anti-aliased. Just turn Anti-Aliasing off, at least for smaller fonts. 
Other than this, i cannot see something blurred on your screenshot. ;-)

[edit]
If you're using an TFT monitor, you could also try to set the dpi to its native resolution.
[/edit]

---

### Post by Niklas Schröder on 2008-01-10
it's bold and itallic fonts that bother me.  look at the "Gmail: Messages" text.  it's slightly blurry around the edges.  it's not much, but when it's all over the screen it kinda gets to you...

---

### Post by Niklas Schröder on 2008-01-10
fixed it.  disabled the option for sites to use their own fonts in firefox.  ;)

---

### Post by JackTheDipper on 2008-01-10
> **Niklas Schröder said:**
> fixed it.  disabled the option for sites to use their own fonts in firefox.  ;)

to be honest, that doesn't fix the problem, it just reduces the amount of cases that let the problem occur with the effect that websites may not be displayed as they are meant to be by the web designer.
Did you try setting your dpi to your monitors native resolution (like 96dpi on many monitors)? (/me is btw using font sizes of 8pt ;-))
is your problem only firefox-related?

(i still see no blurry on your font, btw... but I'm using a crt monitor and no tft.. here it just looks like anti-aliasing)

---

### Post by Niklas Schröder on 2008-01-10
it seems to be only firefox related strangely enough.  and i haven't noticed any cases of lost design...  yet...  ^_^;

---

