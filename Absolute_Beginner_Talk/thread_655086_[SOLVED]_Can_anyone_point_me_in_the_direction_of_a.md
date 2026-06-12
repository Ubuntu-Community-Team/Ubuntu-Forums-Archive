---
title: "[SOLVED] Can anyone point me in the direction of a good browser besides Firefox or Op"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by fullmetalgerbil on 2007-12-31
I stopped using Firefox because it was crashing frequently and would occaisionally lock up the desktop. Went to Opera, but I dont like it for various reasons though it doesn't crash. 
I've seen people here in the forums mention Ice weasel, but I'm not sure if the iceweasel-torbutton package in synaptic is it. Also I Googled it and went to the Get IceWeasel listing but there was just a big list of terminal commands I didn't feel comfortable copy and pasting.
There's also Iceape in the Add/Remove list, but it comes with a suite that I dont really want and I dont know if its a very good browser.
Any suggestions would be welcome and much appreciated.
and Happy New Year!:)

---

### Post by RomeReactor on 2007-12-31
Hi. You could try [Epiphany]("http://www.gnome.org/projects/epiphany/"); it's in the repositories, so you can look for it in Add/Remove or Synaptic, or to install from the terminal (Applications->Accessories->Terminal):
```
sudo apt-get install epiphany-browser
```

Do a search for **web browser** in Add/Remove; you'll get a few more results. Here's a [Wikipedia entry]("http://en.wikipedia.org/wiki/List_of_web_browsers_for_Unix/Linux") for Linux browsers.

---

### Post by doorknob60 on 2007-12-31
Epiphany is pretty nice, it's easy to use and fast and my second favorite Linux browser (besides Firefox).

EDIT: Rome beat me :(

---

### Post by Dr Small on 2007-12-31
w3m is awesome, but it's command line interfaced :)

---

### Post by alx010 on 2007-12-31
I'm pretty new to all this myself, & was having problems with Firefox being slow, & using a lot of cpu. Yesterday I decided to try Swiftfox, & it seems to have solved a lot of problems. Pages load quicker, & I don't have the cpu spikes I was having before.

If you decide to try it though, make sure you get the package that has been optimized for your processor. Good Luck! :)

---

### Post by PmDematagoda on 2007-12-31
[Kazehakase]("http://kazehakase.sourceforge.jp/") is not too bad itself. It can be installed using:-
```
sudo apt-get install kazehakase
```

---

### Post by fullmetalgerbil on 2007-12-31
Epiphany is ok, though if I use it I'm going to miss the ease of a search bar being right there. Opera is just annoying to me, the built in Bit Torrent client hijacks my torrent files so I cant even use my desktop client. Thats really the biggest thing, plus I just miss all my Firefox extentions *sob*. Thats why I was asking about IceWeasel, since its a Mozilla offshoot I thought there might be useful add-ons for it.

---

### Post by jken146 on 2007-12-31
In epiphany you can type your google search string in the address bar.

---

### Post by Crumpets and Jam on 2007-12-31
> **PmDematagoda said:**
> [Kazehakase]("http://kazehakase.sourceforge.jp/") is not too bad itself. It can be installed using:-
```
sudo apt-get install kazehakase
```

I like this one too.

---

### Post by Tux.Ice on 2007-12-31
i think netscape navigator can be used in linux or there is seamonkey (like firefox)

---

### Post by Dr Small on 2007-12-31
Also, to help speed things up, disable IPv6 ;)
[http://ubuntuforums.org/showpost.php?p=4034522&postcount=4](http://ubuntuforums.org/showpost.php?p=4034522&postcount=4)

---

### Post by fullmetalgerbil on 2007-12-31
I'm interested in trying out all of these recommendations, so far I've found Epiphany and Kazehakase to be ok, Seamonkey I haven't tried yet, and Netscape Navigator is downloaded and sitting on my desktop with me not knowing how to install it. I downloaded it via the archive manager and I'm wondering if a sudo install netscape-navigator-9 command in terminal would do the trick. Its a .tar file.
Sorry if I'm sounding picky or difficult over a stupid browser, I just want to find something I like and will want to keep for a long time that works well with flash and doesn't crash. Both Epiphany and Kazekahase see very stable and they work well with flash, and as I dont need a browser with an email client or HTML scripting doo dads so I doubt I'll be using Seamonkey. But I do want to try Netscape Navigator since I used to use it back in the day before I had my Luddist phase and didn't use computers for about a decade. I know there's tons of browsers out there and I'm not, like, going to try every last blasted one of them and keep wasting space here posting about it. I just wanted a few recommendations I could try out.
Where I'm stuck though right now is what to do with this Netscape .tar file on my desktop.

---

### Post by fullmetalgerbil on 2007-12-31
Oh, and Firefox just crashes when I enter about config into the URL bar to disable IPv6. I appreciate that you tried to help though.

---

### Post by Sef on 2007-12-31
> Netscape Navigator is downloaded and sitting on my desktop with me not knowing how to install it.

[Netscape Navigator]("http://www.news.com/underexposed/8301-13580_3-9838145-39.html?tag=nefd.top") has been discontinued.   Updates and security patches will no longer be developed for it as of 1 Feb 2008.

---

### Post by GSF1200S on 2007-12-31
If youre tired of the crashes and freezing, but still like the extension base and want it optimized for your processor, I would suggest Swiftweasel. It runs fast and stable- at least try it..

---

### Post by fullmetalgerbil on 2007-12-31
I've ditched the Netscape navigator file and am going to try swiftweasel now. Hopefully I'll be able to install it.

---

### Post by fullmetalgerbil on 2007-12-31
Maybe I'm getting off track here, but I went to try and get swiftweasel (the last browser I'm going to try out) and according to the site I have to start a new reposittory in my sources to download and install it. I'm not quite sure what I'm doing here and I dont want to eff things up. If anybody could help me I would much appreciate it so I can finally pick which browser I'm going to use.

---

### Post by GSF1200S on 2007-12-31
> **fullmetalgerbil said:**
> Maybe I'm getting off track here, but I went to try and get swiftweasel (the last browser I'm going to try out) and according to the site I have to start a new reposittory in my sources to download and install it. I'm not quite sure what I'm doing here and I dont want to eff things up. If anybody could help me I would much appreciate it so I can finally pick which browser I'm going to use.

Or you could go here and download the .deb ;)

[http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473)

---

### Post by oldos2er on 2007-12-31
Flock. [http://www.brothersoft.com/flock-for-linux-download-61472.html](http://www.brothersoft.com/flock-for-linux-download-61472.html)

---

### Post by fullmetalgerbil on 2008-01-01
I downloaded Swiftweasel and installed it, all my beloved Firefox extentions appeared. As long as it doesn't crash like Firefox did everything will be swell. I didn't get the chance to try Flock or Seamonkey, but for now thread solved. Thanks everybody for your helpful recommendations, I hoist a tankard of Ubuntu and sat "Cheers!" to ya's!

---

### Post by RomeReactor on 2008-01-01
To add the SwiftWeasel repository, open Synaptic (System->Administration->Synaptic), go to "Settings->Repositories" and on the second tab (Third-Party Software) press the "Add" button and enter the following line:
```
deb http://download.tuxfamily.org/swiftweasel gutsy multiverse
```
close the repositories window and, still in Synaptic, press the blue "Reload" button. You can then find SwiftWeasel in Add/Remove, Synaptic, or install it from the command line with apt-get or aptitude.

EDIT: Posted late. In any case, having the repository means that whenever there's an update to SwiftWeasel, you'll be notified of it along with the rest of Ubuntu's updates, instead of having to check their site for a new release.

---

### Post by GSF1200S on 2008-01-01
> **RomeReactor said:**
> To add the SwiftWeasel repository, open Synaptic (System->Administration->Synaptic), go to "Settings->Repositories" and on the second tab (Third-Party Software) press the "Add" button and enter the following line:
```
deb http://download.tuxfamily.org/swiftweasel gutsy multiverse
```
close the repositories window and, still in Synaptic, press the blue "Reload" button. You can then find SwiftWeasel in Add/Remove, Synaptic, or install it from the command line with apt-get or aptitude.

EDIT: Posted late. In any case, having the repository means that whenever there's an update to SwiftWeasel, you'll be notified of it along with the rest of Ubuntu's updates, instead of having to check their site for a new release.

Agreed. You can use apt to remove swiftweasel- simply search in adept or add/remove and it should be there. I say use the deb until you are sure its good enough, and then go this route so apt will keep it up to date.

---

### Post by jfank on 2008-01-01
I've been interested in different web browsers, but FF is still my fav.  I installed this SwiftWeasel and it is pretty cool.  Thank you for having this thread on here.  It gave me a couple of different browsers to try out.

---

### Post by HermanAB on 2008-01-01
Hmm, 'links' is rock solid, lightning fast and never crashes:
[http://links.sourceforge.net/](http://links.sourceforge.net/)

It should be in synaptic.

Cheers,

Herman

---

### Post by doorknob60 on 2008-01-01
I don't think he's looking for a terminal-based browser though.

---

### Post by GSF1200S on 2008-01-01
To the OP- let us know if Swiftweasel does the trick for you... Im curious to know how it works compared to vanilla Firefox.. (works awesome for me- I had to use it as im on 64bit for java)

Theres also swiftdove, iceweasel, and other optimized builds that might do the trick...

---

### Post by fullmetalgerbil on 2008-01-01
Swiftweasel is working fabulously. Its only become non responsive once since I installed it and it didn't lock up the whole desktop like Firefox used to do. Also, because I still have Firefox installed as a secondary Swiftweasel came up with my extentions auto loaded. The only thing now is I'm not sure how to set Swiftweasel so it will come up when I click links in email and such. Right now when I do it Firefox automatically comes up. Do I have to just make Swiftweasel my default browser? I tried doing that when I was still using Opera (yick) and Firefox would still handle the email links.

---

### Post by benny bronx on 2008-01-01
You may want to try the Opera beta 9.5 if your problem with opera was performance,  I have found it very stable and faster than the one in the repo so far.

---

### Post by Yoshiman007 on 2008-01-01
To add my two cents, I've been using Swiftweasel for a couple of months with only minor problems with the Download box causing slowdowns. That won't apply to all machines as mine is exceptionally slow/old (IBM thinkpad single core laptop). I do have one question for any Swiftweasel users though: just today it seems that Wikipedia of all things is having problems. Opera and Firefox still display it properly, but it seems like Swiftweasel is not displaying it with full graphics, images, etc. I'll keep tinkering with it for now, but any input/suggestions would be appreciated. Other than that, I highly recommend Swiftweasel.

It appears that Swiftweasel has fixed itself, so I'm now full ahead for Swiftweasel!

---

