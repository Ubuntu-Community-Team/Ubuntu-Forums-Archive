---
title: "Thunderbird as default"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by The Hedgehog on 2005-10-09
When I right click on an item, I have the opportunity to send it through e-mail via Evolution.
The problem is that I don't use Evolution but Thunderbird.
I've already set Thunderbird as default(System=>Preferences) but I still can't choose Thunderbird.
How do I change this?

---

### Post by aysiu on 2005-10-09
Did you install Thunderbird from the Mozilla .tar.gz or through Synaptic/apt-get?

---

### Post by The Hedgehog on 2005-10-10
via synaptic

---

### Post by aysiu on 2005-10-10
Is there anywhere where you can manually type in the path to Thunderbird (as opposed to picking it as an option from a drop-down menu)?

---

### Post by mike984 on 2005-11-09
Has this been answered anywhere else because I can't find it.  I too am not able to right-click on a file and choose Thunderbird.  It only allows Evolution.  Thunderbird is my default.  Does anyone have a fix?

---

### Post by aysiu on 2005-11-10
Here's the fix (see screenshots).

---

### Post by mike984 on 2005-11-13
Hello,

Thanks for your quick reply.  However, I did that and Evolution is still the only item that appears when I right-click on an item to "Send to".  When I right-click and choose Send to.. mail recipient, the down arrow to choose my mail client only shows Evolution.  I did make Thunderbird my preferred mail app and it didn't anything.  Any other suggestions?  Has anyone had this problem before?

---

### Post by popeye on 2005-11-13
Did you already try do it the way from the official ubuntu guide

[http://help.ubuntu.com/starterguide/C/ch09.html#id2540894](http://help.ubuntu.com/starterguide/C/ch09.html#id2540894)

> 9.12. 	How can I change my preferred email client to Mozilla Thunderbird?
	
   1.      To install Thunderbird, see How do I install the Thunderbird email client?
   2.      Choose System->Preferences->Preferred Applications.
   3.      Click on the Mail Reader tab, and select the Custom option.
   4.      In the Command text box, type mozilla-thunderbird %s, then close the dialog.

This worked for me. Goodluck

---

### Post by mike984 on 2005-11-14
I just tried and when I right-click a file in Nautilus, it still only allows me to choose Evolution.  Everything else in Ubuntu has worked so well.  I can't understand why this isn't.  Is there a registry setting that perhaps needs changing?

---

### Post by Alpha_Maverick on 2006-03-09
Any news? I'm also having this problem, and nothing is helping.

---

### Post by Gordonbp531 on 2006-03-10
there isn't a fix. I've contacted the author of the Nautilus plug-in that allows the "right-click send-to" context menu and there is nothing that can be done to fix it. (I can't remember whether he said that he was working on an up-dated version of it or not....)
Irritating, isn't it?
I've come across another limitation - if you click the "Mail" icon in Open Office, then it opens up a Compose Window in Thunderbird OK, bit no document in the body or attachment. If you have Evolution as preferred email client, then it works OK.....
Looks like Evolution is really embedded into the system.....

---

### Post by Megapearl on 2006-04-19
I'm having exactly the same problem, anyone??

---

### Post by aysiu on 2006-04-19
[QUOTE=Megapearl]I'm having exactly the same problem, anyone??[/QUOTE] Maybe you can symlink Thunderbird to /usr/bin/evolution (or wherever the Evolution launcher is). That way, when it calls Evolution, it'll really be calling Thunderbird.

---

### Post by danielph on 2006-05-12
[QUOTE=aysiu]Maybe you can symlink Thunderbird to /usr/bin/evolution (or wherever the Evolution launcher is). That way, when it calls Evolution, it'll really be calling Thunderbird.[/QUOTE]
I would also like to get this working. I tried symlink, but it just caused Nautilus to crash. Has someone filed a bug for this?


Regards

Dan

---

### Post by androxxl on 2006-06-06
hello!
I did make Thunderbird my preferred mail app and it didn't anything.
When I right-click and choose Send to.. mail recipient, the down arrow to choose my mail client only shows Evolution. How can I fix this?
I use dapper drake 6.06

---

### Post by Stew2 on 2006-06-06
[QUOTE=androxxl]hello!
I did make Thunderbird my preferred mail app and it didn't anything.
When I right-click and choose Send to.. mail recipient, the down arrow to choose my mail client only shows Evolution. How can I fix this?
I use dapper drake 6.06[/QUOTE]

So you clicked on <System> then <Preferences> then <Preferred Applications> and switched your mail reader to "Mozilla Thunderbird" (as per screen shot) and it still doesn't work? I just did this to mine as it was defaulting to "Evolution" as well and it fixed it so that it now chooses "Thunderbird" when I right click a link to send it. This should work for you too. I am also using Dapper. Hope this helps!
[ATTACH]10753[/ATTACH]
Regards,
Stew2

Edit: Whoops! I guess I should read all the posts before replying. Aysiu had already covered this :), my bad.

---

### Post by Stew2 on 2006-06-06
Perhaps I spoke too soon! :) 
If I am on a web page and I right click on something now it brings up a Thunderbird send box, but if I have a file on my desktop (ie. the screenshot pic) and I right click on that it brings up an Evolution send box. How strange. Must be a bug or something, you would think it would perform the same action whether you are on the internet of just on your desktop? Works OK for me because I send most my links etc. from web pages, but the inconsitency is a little strange. I will have to poke around with it a little more. :D 

Regards,
Stew2

---

### Post by androxxl on 2006-06-07
The same problem is in my case. So newer mind. Thank´s anyway. :)

---

### Post by krizz on 2006-10-27
You can try this [http://www.ubuntuforums.org/showthread.php?t=26117&highlight=nautilus+send+thunderbird](http://www.ubuntuforums.org/showthread.php?t=26117&highlight=nautilus+send+thunderbird)

---

