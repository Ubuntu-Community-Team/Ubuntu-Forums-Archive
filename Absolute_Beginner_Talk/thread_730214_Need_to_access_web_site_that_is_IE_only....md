---
title: "Need to access web site that is IE only..."
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by MacKai on 2008-03-20
I am trying to migrate to Ubuntu however my first stumbling block is a work site (that I can't give out)
that won't run correctly on Fire Fox. It is unfortunate, and I have talked to the I.T. department and they refuse to change any thing so lets get passed all that.

how do I get I.E to run either in Ubuntu Fire Fox or Ubuntu.... or is there any other route

also I'm a complete newbie so lets keep it as simple as possible please....

thanks in advance... 

MacKai

---

### Post by halitech on 2008-03-20
there used to be an add on called user agent switching (not sure if its still going) but you could try to get it and use it to fool the website into thinking you are running IE

edit: just checked and it is
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by wolfen69 on 2008-03-20
you could install virtualbox and run xp in that.

---

### Post by upbeat.linux on 2008-03-20
Do you have the URL for the site or know the name of the application you are trying to connect to? That would help us narrow down how to help you.

Remarks:

1. As noted above: try using Firefox user agent switch: [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59) and change the agent from Firefox to IE

2. You could install IE in wine and log into the site that way

3. Try using IE Tab: [https://addons.mozilla.org/en-US/firefox/addon/1419](https://addons.mozilla.org/en-US/firefox/addon/1419) 

I'm not sure if option 3 runs on Ubuntu.....too lazy to check right now.

Also, there's a tutorial here that might help you out with option #2:

[http://www.ubuntugeek.com/running-internet-explorer-in-ubuntu-linux.html](http://www.ubuntugeek.com/running-internet-explorer-in-ubuntu-linux.html)

---

### Post by Linux_Man on 2008-03-20
If you have a license for Windows IE will run in Wine (some versions). Also try some other Free browsers such as Konqueror, it might render correctly, Opera is another shot and see if those work. If not, install Windows in Virtual Box and see if that works.

---

### Post by fela on 2008-03-20
> **Linux_Man said:**
> If you have a license for Windows IE will run in Wine (some versions). Also try some other Free browsers such as Konqueror, it might render correctly, Opera is another shot and see if those work. If not, install Windows in Virtual Box and see if that works.

I was just gonna say, there is a nice guide/howto of getting IE running on linux at ies4linux.org, I don't know whether i could trust it though

What I'd do is use Wine-doors to install IE

---

### Post by MacKai on 2008-03-20
well i tried the first solution User Agent Switcher  but it didn't work.

 i cant give out the site - i know thats frustrating- but the issue is that it doesn't render correctly.

 i hover over a link and the drop down list does not appear directly below so i can select from the list. instead it appears in the upper left corner of the window where i cant get to it.. also just general rendering issues (overlapping text and elements) 

the wine option looks like it's over my head, but if no other option presents it's self i'll figure it out...

MacKai

---

### Post by Linux_Man on 2008-03-20
Have you tried other browsers? Opera, Konqueror, Galeon and other browsers are in the Ubuntu repos and might render it correctly,

---

### Post by cybergalvez on 2008-03-20
> **MacKai said:**
> I am trying to migrate to Ubuntu however my first stumbling block is a work site (that I can't give out)
that won't run correctly on Fire Fox. It is unfortunate, and I have talked to the I.T. department and they refuse to change any thing so lets get passed all that.

how do I can get I.E to run either in Ubuntu Fire Fox or Ubuntu.... or is there any other route

also I'm a complete newbe so lets keep it as simple as possable please....

thanks in advance... 

MacKai

if its for work and its IE only I'd bet its some stupid activeX thing which most likely won't work outside of Windows and IE.  If you have an XP install disk around your best bet is to use virtualbox and install XP in that.  Then you can just run XP adn IE for your work stuff.  Thats at least what I do
Jose

---

### Post by fela on 2008-03-20
> **MacKai said:**
> the wine option looks like it's over my head

you know, wine isn't that hard (if at all) to configure, I could actually include a quick howto in this post:

1) ```
sudo apt-get install wine
```

2) download wine doors (e.g. from [it's website]("http://www.wine-doors.org/wordpress/?page_id=3"))

3) assuming you downloaded the .deb, open it with deb installer app and click install

4) run wine doors (should come up in menu) and configure it...sometimes it hangs in this process, if it hangs for more than an hour I reccomend force quitting it and seeing if it works

5) run wine doors again and look for IE, press install, voialla, after install it should work :)

or you could justuse the script at ies4linux.org...

---

### Post by muadnu on 2008-03-20
I have used  [http://www.tatanka.com.br/ies4linux/page/Main_Page]("http://www.tatanka.com.br/ies4linux/page/Main_Page") in the past to install IE6 with wine, and it has run fine for me, it only tends to flicker a lot when there's flash in a webpage, which I've seen every time I install IE via wine. I've only used it briefly when there's no other choice, so it's not that bad.... I'n not sure about the activeX controls, but you could give it a shot...

---

### Post by MacKai on 2008-03-20
tried the IEs4linux option and cant get it to work, I get this error at the end..

You need to install wine first!
download it here: http:[www.winehq.org](www.winehq.org)

i'm sure i'm doing something wrong but ...

im just to new i guess.. i need to learn this all eventually , no time like the present..
 
any ideas

MacKai

---

### Post by Linux_Man on 2008-03-20
Just type in "sudo apt-get install wine" and you will have Wine. Then try running it again.

---

### Post by muadnu on 2008-03-20
Did you install wine? You definitely need it for ies4linux to work. If you did install it, it would be weird that you get that error. If you didn't, run this at the terminal
```
sudo apt-get install wine
sudo apt-get install cabextract
```
(ies4linux also needs cabextract) and then try the ies4linux script...

---

### Post by AmyRose on 2008-03-20
Yeah, I'd go along with those who recommended ies4linux. Installing a copy of Windows XP isn't always feasible (or legal, if you don't have a copy of it ;) ), and it's way too much for just using a particular website.

Make sure you have the Universe enabled before using apt-get to install Wine.

---

### Post by jimv on 2008-03-20
Go get IEs4Linux and stop suffering!

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by Steve Angelidis on 2008-03-20
Being fabulously wealthy and a Linux newbie, I forked out $40 for CrossOver Linux from [http://www.codeweavers.com/]("http://www.codeweavers.com/"). It includes Wine in an easy to install package. You can then download, install and run IE 6 and a number of other Windows applications.

Easy if you've got $40 to spare. You can try it free for 30 days.

---

### Post by Joe Dinmore on 2008-03-20
I recommend that you try Opera web browser. It can fool sites into thinking you are running IE. It's also a very good browser, which I find to be faster than Firefox 2.x.

---

### Post by |{urse on 2008-03-20
[http://www.tatanka.com.br/ies4linux/page/Installation]("http://www.tatanka.com.br/ies4linux/page/Installation") <--------------------------------------------------------------------------------------------------------------------------------------------------->

---

### Post by jimv on 2008-03-21
I didn't notice that you already tried IEs4linux

open a console and type

[INDENT]sudo apt-get install wine[/INDENT]

then try install ies4linux

---

### Post by nexus_2006 on 2008-03-21
I have 2 or 3 IE only sites for my Uni. that work just fine in Opera.  I get kicked out at the door if I try it normally, but in Opera under site preferences you can set it to mask as IE and I have found that this lets me in any site that I have needed in that requires IE only including bank sites and the secure sites on campus I talked about.  Might be worth a shot.

---

### Post by stchman on 2008-03-21
> **MacKai said:**
> I am trying to migrate to Ubuntu however my first stumbling block is a work site (that I can't give out)
that won't run correctly on Fire Fox. It is unfortunate, and I have talked to the I.T. department and they refuse to change any thing so lets get passed all that.

how do I can get I.E to run either in Ubuntu Fire Fox or Ubuntu.... or is there any other route

also I'm a complete newbe so lets keep it as simple as possable please....

thanks in advance... 

MacKai

There is a program called ies4linux.

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

It actually installs IE6 and runs it on Linux.

---

### Post by stchman on 2008-03-21
> **upbeat.linux said:**
> Do you have the URL for the site or know the name of the application you are trying to connect to? That would help us narrow down how to help you.

Remarks:

1. As noted above: try using Firefox user agent switch: [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59) and change the agent from Firefox to IE

2. You could install IE in wine and log into the site that way

3. Try using IE Tab: [https://addons.mozilla.org/en-US/firefox/addon/1419](https://addons.mozilla.org/en-US/firefox/addon/1419) 

I'm not sure if option 3 runs on Ubuntu.....too lazy to check right now.

Also, there's a tutorial here that might help you out with option #2:

[http://www.ubuntugeek.com/running-internet-explorer-in-ubuntu-linux.html](http://www.ubuntugeek.com/running-internet-explorer-in-ubuntu-linux.html)

IETab will only run on a Windows machine.

---

### Post by MacKai on 2008-03-25
sorry it took me so long to get back to this...


well i tried :


Code:

sudo apt-get install wine
sudo apt-get install cabextract

and get 


something about "can not find package" 

so i went to the appropriate web sites and 

down loaded the packages every thing looked ok 

but then went back to 


Code:

sudo apt-get install wine
sudo apt-get install cabextract

 and i get something about "broken packages" 

i got to run. hope to be back on this tonight but probably tomorrow....

MacKai

---

### Post by neobuddha on 2008-03-25
Here is what I did. I installed wine which works also for some other windows applications and some games.then I downloaded ies4linux and installed that with wine.It works perfectly  .I personly don't like ie explorer at all.But as you discovered ,some websites still force you to use to acess thier site.I hope this helps.

---

### Post by MacKai on 2008-03-25
well tried agin to install wine

from the wine web site:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- 

then

sudo apt-key add -

this seems to go well 

then 

sudo apt-get install wine

i get this 

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
E: Broken packages
ubuntu@ubuntu:~$ 


i go ahead and:

sudo apt-get install cabextract:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
cabextract is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 89 not upgraded.


this looks good...

ill try again tomorrow 

any suggestions?

MacKai

---

### Post by neobuddha on 2008-03-26
> **MacKai said:**
> well tried agin to install wine

from the wine web site:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- 

then

sudo apt-key add -

this seems to go well 

then 

sudo apt-get install wine

i get this 

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
E: Broken packages
ubuntu@ubuntu:~$ 


i go ahead and:

sudo apt-get install cabextract:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
cabextract is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 89 not upgraded.


this looks good...

ill try again tomorrow 

any suggestions?

MacKai



A friend had the same problem and solved it by downloading a slackware package of wine(I don't know where from).I think it's in the format .tar.gz. He converted it to a .deb package using alien.It install without any complaints.Idon't know if this will help in your case.If you don't have alien installed, get it with this command.sudo apt-get install alien.It is a very useful program.

---

### Post by dcstar on 2008-03-26
> **MacKai said:**
> 
.........
The following packages have unmet dependencies:
  wine: Depends: **binfmt-support** (>= 1.1.2) but it is not installable
E: Broken packages
........
any suggestions?

MacKai

Go into Synaptic, and enable the "Universe" repositories, then reload and manually install that package.

---

### Post by nutz on 2008-03-26
This is really lame. U of P does the same thing. They won't let you view certain parts of their site unless you are using IE.

---

