---
title: "ed2k links not processed by firefox to amule"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-12
Hi,

I have firefox and amule installed through synpatic.

I have followed the instructions on this page:
[http://www.amule.org/wiki/index.php/Ed2k_links_handling#Mozilla_1.7_(or_later)_&_Firefox_0.9_(or_later)](http://www.amule.org/wiki/index.php/Ed2k_links_handling#Mozilla_1.7_(or_later)_&_Firefox_0.9_(or_later)))

I have restarted firefox and amule and still firefox refuses to process the link to amule.

"Firefox doesn't know how to open this address, because the protocol (ed2k) isn't associated with any program."


about:config

network.protocol-handler.external.ed2k     user set     boolean       true
network.protocol-handler.app.ed2k     user set     string       usr/bin/ed2k

I don't know why this isn't working.

Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-15
Anyone?

---

### Post by catlett on 2006-06-15
I don't know but I would trouble shoot with galeon, for 2 reasons. One it's based on gecko and 2 it's in the repositories.
The link you posted has a galeon how to as well. So I guess I would try galeon and see if I could get it working and then see what was different between the 2.
Even if galeon only worked it's a pretty cool browser and it's open source. Good luck.

---

### Post by u.b.u.n.t.u on 2006-06-15
Thanks for the suggestion catlett.

---

### Post by catlett on 2006-06-15
I see you around but I haven't had a chance to reply to anything. You're always giving answers instead of asking questions! :D  It appears your transition has been a quick one.

P.S. Just in case you haven't come across it yet, this is the guide I use for new installs. It is well written and straight forward. I know you're going to be doing alot of installs shortly so I thought I would throw it out there in case you haven't already seen it. [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)  See you around.

---

### Post by u.b.u.n.t.u on 2006-06-15
[QUOTE=catlett]I see you around but I haven't had a chance to reply to anything. You're always giving answers instead of asking questions! :D  It appears your transition has been a quick one.

P.S. Just in case you haven't come across it yet, this is the guide I use for new installs. It is well written and straight forward. I know you're going to be doing alot of installs shortly so I thought I would throw it out there in case you haven't already seen it. [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)  See you around.[/QUOTE]

Thanks catlett :D

---

### Post by boilerlinux on 2006-10-25
Greetings!

I'm new (again) to linux and i'm encountering the same problem as described in the first post of this thread.

has there been a solution to this?

thx in advance

---

### Post by s2d4 on 2006-10-31
mine used to work before updating to edgy a few days ago. the reason why it isnt working on my comp is because the ed2k file in /usr/bin/ no longer exists. If i remember correctly, there used to be a package called amule-ed2k that takes care of that. However, I have no been able to find it anywhere.

---

### Post by SongQi on 2006-10-31
I don't know if this helps anybody out, but what I've been doing is doing a right-click "View source" for whichever page has the ed2k link in it from which I want to download. Once the source is up on the screen, I search through the code for "ed2k://"  and then copy the link that corresponds to what I want to download and paste it into AMule's ED2K Link Handler bar.  Then, I just click "Commit".  Amule accepts that just fine.  Hope that helps somebody.

---

### Post by bassliu on 2006-11-03
u can install a extra package amule-utils via apt-get
```
sudo apt-get install amule-utils
```

then set the network.protocol-handler.app.ed2k to usr/bin/ed2k in about:config

good luck:)

---

### Post by araz on 2006-11-08
This solution worked for me: 
> Just go to about:config, right click and new->string. Input network.protocol-handler.app.ed2k as name and ed2k as value.
in [http://ubuntuforums.org/showthread.php?t=153592&highlight=firefox+ed2k](http://ubuntuforums.org/showthread.php?t=153592&highlight=firefox+ed2k)

---

### Post by Hellaxe on 2006-12-10
It doens't work here.

---

### Post by araz on 2006-12-12
Do you have amule-utils installed?

---

### Post by Hellaxe on 2006-12-18
Yes i do. But i think this is a problem with Edgy because de package ed2k is missing from everywhere.

---

### Post by araz on 2006-12-18
The ed2k is in the package amule-utils for edgy. You can see [here]("http://packages.ubuntu.com/edgy/x11/amule-utils").

my about:config with ed2k filter is shown in thumbnail. how is yours?:

---

### Post by Hellaxe on 2006-12-19
Thanks mate. It works now. Somehow i missed that package and installed the gui version.

This is because i've made the installation through Automatix and it only installed the amule program.

By the way i've got a version of Amule compiled for Dapper. Does it work in Edgy. I didn't try it because of the risk of mess up with my system.

Thank you

---

### Post by CyberCod on 2007-01-01
Just to clarify.... 

one should have the following packages installed

```

amule
amule-utils

```

and not

```

amule-utils-gui

```

one should then proceed to open Firefox (or Swiftfox or Flock?) and type in the address bar:


```
about:config 
```

and hit enter, whereupon a page will load with a Filter box and several colums of data.

R-click one of the entries in the data table (any one) and click "New   >" then click "Boolean".

Enter into the Preference box:

```

network.protocol-handler.external.ed2k

```

Click OK.

Select "true" and click OK.

Then r-click one of the entries in the data table (any one) and click "New   >" then click "String".

Enter into the String box:

```

network.protocol-handler.app.ed2k

```

Click OK.


This is where I have questions.

Is it..

A.

Enter into the string value box:
```
ed2k
```


B.

Enter into the string value box:
```
usr/bin/ed2k
```

or C.
Enter into the string value box:
```
/usr/bin/ed2k
```
(I would have figured it would need that slash there)

Or are they all the same?

I'm just wanting to be able to refer back to this page later.  I'm installing a lot of linux machines lately... currently 6 so far, about to be 7.  I've installed Ubuntu, Kubuntu, Edubuntu and Xubuntu, using alternate CD for Xubuntu (great  for low RAM systems) and used LiveCD for all the others.

Whats crazy is it's about to speed up!  Lots of custom build jobs coming in tax season.

Sorry for rambling... it is New Years Eve, my mind is not what it should be right now. :D

---

### Post by Griffin3 on 2007-02-08
It should be /usr/bin/ed2k on a normal Ubuntu install.  To be sure, just go to a terminal window, and type
```

which ed2k

```If it does return something similar to /usr/bin/ed2k, you probably don't have amule-utils installed.

---

### Post by jlavrador on 2007-04-01
Thanks for your help I had configures the about:config in Firefox but the links didn't work and after install the amule-utils, the /usr/bin/ed2k was created and the links are working now.

Best regards :)

---

