---
title: "Installing sun-java5 Error"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by ravenproject_two on 2006-06-29
Hello-I just started using Linux a couple days ago-
I need to install sun-java5; actually because I want to get LimeWire...so I opened konsole and entered in:

sudo apt get-install sun-java5-bin  

and I got an error message saying:
E: Couldn't find package sun-java5-bin

What am I doing wrong?  How can I get and install the java5 package?****

---

### Post by amohanty on 2006-06-29
I dunno about dapper but in breezy sun-java is not available in the repos. One of my previous posts outlines how to get and install jre in breezy:

[http://www.ubuntuforums.org/showpost.php?p=567769&postcount=2](http://www.ubuntuforums.org/showpost.php?p=567769&postcount=2)

HTH
AM

---

### Post by ravenproject_two on 2006-06-29
What is the  "repos"?  Can anyone help me w/ installing on dapper?  keep in mind that I am a cpu dummy-I have only converted to Ubuntu (From Xp Home) a couple days ago...I learn quick though-you'll never have to tell me twice

---

### Post by amohanty on 2006-06-29
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

HTH
AM

---

### Post by ravenproject_two on 2006-06-29
Okay-I checked out the "Repos" link you gave me-now I am learning a little bit...still doesn't help w/ the getting/installing sun java5..any help?  Anything is always appreciated....
-The RavenProject:confused: ****

---

### Post by amohanty on 2006-06-29
Did you look at the link included in my previous email?

AM

---

### Post by ravenproject_two on 2006-06-29
Yeah I went to that link but it doesn't help me because I do not know how to:
 
"add the following to /etc/apt/sources.list -
Quote:
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free"

Hold on.....
Ok-I have figured out how to open that source.list
...now how do I add those links?  Just copy and paste them? or do I have to write in anything extra?  Thanks for your patience...O:)****

---

### Post by ravenproject_two on 2006-06-29
By the way-I think I got what your insttructions meant to just copy/paste those links into the sources.list but the list is a read only file so how do I get around that? Sorry:confused: ****

---

### Post by sas on 2006-06-29
If you are using the latest version of Ubuntu (6.06LTS aka dapper) see [https://help.ubuntu.com/kubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/kubuntu/desktopguide/C/extra-repositories.html) to enable the "multiverse" repository. Then try to install sun-java5-bin

---

### Post by ravenproject_two on 2006-06-29
Okay I did what you what the link said and entered the multiverse...then I tried to install sun java5 again and it gave me the same message...E: Couldn't find package sun-java5-bin??:confused: :confused: ****  What am I doing wrong?

---

### Post by sas on 2006-06-29
Does running "sudo apt-get update && sudo apt-get install sun-java5-bin" help anything?

how about "apt-cache search sun-java5" ?

---

### Post by ravenproject_two on 2006-06-29
=D> Sas you are a beast!!!  It worked and konsole is busy installing sun-java5-bin right now...what did you tell me to do so I know?  Thank you so much-I have been at this for hours already today!  Now all I have to do is figure out how to install Limewire...I already installed alien earlier...nothing is working but I will jump to a Limewire forum for that and quit pestering you folks...Thanks so much

---

