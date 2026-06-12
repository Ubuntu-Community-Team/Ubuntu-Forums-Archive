---
title: "Failed to fetch - Update"
date: 2013-12-21
forum: Any Other OS
---

### Post by thisisdexter on 2013-12-21
Hello,

I am a returning user to Linux. I hope someone can guide me. I installed Linux Mint 16. Everything went well. I updated it. All good.

I get this error though after updating.

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

I shoud mention I can open [http://security.ubuntu.com/ubuntu/dists/saucy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/saucy-security/Release.gpg) in the browser and view the signature. I have seen that InRelease does NOT exist in the saucy-security distro.

Here is the output of **inxi -r**

```
Repos:     Active apt sources in file: /etc/apt/sources.list.d/official-package-repositories.list
           deb http://packages.linuxmint.com petra main upstream import
           deb http://extra.linuxmint.com petra main
           deb http://archive.ubuntu.com/ubuntu saucy main restricted universe multiverse
           deb http://archive.ubuntu.com/ubuntu saucy-updates main restricted universe multiverse
           deb http://security.ubuntu.com/ubuntu/ saucy-security main restricted universe multiverse
           deb http://archive.canonical.com/ubuntu/ saucy partner
```

My software sources by default are:

```


**Mirrors** 

Main (Petra) http://packages.linuxmint.com (US Server)

Base (Saucy) http://archive.ubuntu.com/ubuntu (UK Server)


```

I would really really really appreciate any help.

My sincerest regards and happy holidays people.

Cheers!

---

### Post by oldos2er on 2013-12-21
Moved to Other OS/Distro Support.

---

### Post by plucky on 2013-12-21
> deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security main restricted universe multiverse
           deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) saucy partner

These repos don't look right,they seem to have an extra / in the lines.

I think they should be ```
deb http://security.ubuntu.com/ubuntu saucy-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu saucy partner
``` without the / after "ubuntu" as in the previous lines.

Good Luck

---

### Post by oldrocker99 on 2013-12-21
+1

---

### Post by thisisdexter on 2013-12-21
Hi,

My sincerest thanks to you my friend.

So I went to Software Manager and deleted the line with the extra '/' and added a new one. Just made changes for the scurity package.

Now I am getting this. It is weird! :(

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/saucy/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/saucy/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by deadflowr on 2013-12-21
> [COLOR=#000000]So I went to Software Manager and deleted the line with the extra '/' and added a new one. Just made changes for the scurity package.[/COLOR]

That seems to be nonsensical.
What do mean by this?
You deleted the / and then added a new one?

plucky's lines are exactly as they should appear in the sources.list file.

What do your's look like.

---

### Post by plucky on 2013-12-21
Did you add the Saucy repos manually?

Does  Mint use the Ubuntu repos by default?

Post output for ```
cat /etc/apt/sources.list
```


> Mirrors 

Main (Petra) [http://packages.linuxmint.com](http://packages.linuxmint.com) (US Server)

Base (Saucy) [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) (UK Server)

How are you using UK and US servers at the same time?

---

### Post by thisisdexter on 2013-12-21
Hi

Thank you so much gentlemen again.

Sorry been headbanging - (Courtesy Heavy Metal and forgot looking at the thread) :D

Now headbanging solving this issue - Figuratively.

> **deadflowr said:**
> That seems to be nonsensical.
What do mean by this?
You deleted the / and then added a new one?

plucky's lines are exactly as they should appear in the sources.list file.

What do your's look like.

Hi - Thank you so much deadflowr, I appreciate your response. I added the lines exactly as mentioned above. Here look at the screenshot Attached. I deleted the line with extra '/' and added one exactly the same because when I was editing it, and clicking OK, it was not saving it. So I deleted one and added one exactly the same.

[ATTACH=CONFIG]248799[/ATTACH]


> **plucky said:**
> Did you add the Saucy repos manually?

Does  Mint use the Ubuntu repos by default?

Post output for ```
cat /etc/apt/sources.list
```
How are you using UK and US servers at the same time?

Hi plucky - Thanks man, I attached a screenshot. Mint is Ubuntu based infact the latest distro.

[ATTACH=CONFIG]248800[/ATTACH]

Many thanks if you can tell me how to edit the repos file. I tried to edit using the Ubuntu help but the file opened did not contain any of these links where we get updates from. :(  Infact this is the file I tried to edit before but it does not contain any link as the ones that show up...

Also here is the output of the CAT

```
# deb cdrom:[Linux Mint 16 _petra_ - Release i386 20131126]/ saucy contrib main non-free 
deb http://security.ubuntu.com/ubuntu/ saucy-security main restricted universe multiverse 

```

Thank you for your patience.

Cheers!

---

### Post by plucky on 2013-12-21
From your first post

> Active apt sources in file: /etc/apt/sources.list.d/official-package-repositories.list

It seems Mint does it differently to Ubuntu

What does ```
cat /etc/apt/sources.list.d/official-package-repositories.list
``` produce?

---

### Post by thisisdexter on 2013-12-21
Hi

Yes I think you are right, as suggested by you when I added the line it went to the main source file.

Here is the output.

```
deb http://packages.linuxmint.com/ petra main upstream import 

deb http://extra.linuxmint.com/ petra main 

deb http://archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse  
deb http://archive.ubuntu.com/ubuntu/ saucy-updates main restricted universe multiverse 

deb http://archive.canonical.com/ubuntu/ saucy partner  


```

Thank a lot man.

---

### Post by plucky on 2013-12-21
To edit the file use ```
sudo nano /etc/apt/sources.list.d/official-package-repositories.list
``` and remove the extra / from the lines.

To exit and save to the file in nano use Ctrl-O and Ctrl-X.

Also remove the line you added earlier.

Good Luck

---

### Post by thisisdexter on 2013-12-21
Hey man!

Thanks for working with me with so patience...

After editing here is the result:

```


**cat /etc/apt/sources.list**
# deb cdrom:[Linux Mint 16 _petra_ - Release i386 20131126]/ saucy contrib main non-free 

deb http://security.ubuntu.com/ubuntu saucy-security main restricted universe multiverse 


```

AND

```

**cat /etc/apt/sources.list.d/official-package-repositories.list**

deb http://packages.linuxmint.com petra main upstream import 

deb http://extra.linuxmint.com petra main 

deb http://archive.ubuntu.com/ubuntu saucy main restricted universe multiverse  
deb http://archive.ubuntu.com/ubuntu saucy-updates main restricted universe multiverse 

deb http://archive.canonical.com/ubuntu saucy partner  


```


> **plucky said:**
> To edit the file use ```
sudo nano /etc/apt/sources.list.d/official-package-repositories.list
``` and remove the extra / from the lines.

To exit and save to the file in nano use Ctrl-O and Ctrl-X.

Also remove the line you added earlier.

Good Luck


Now the security distro error is GONE!! :D :D

But this :( :

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/saucy-updates/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.


```

Where do I go to edit this?

Thanks a ton...

---

### Post by deadflowr on 2013-12-21
Try adding us to the front of the archive.
(or gb if in Britain, I think...)
so it would look like
```
us.archive.ubuntu.com
```
instead of 
```
archive.ubuntu.com
```
use the same nano command, or you could try a simple one liner
```
sudo sed -i -e 's/archive.ubuntu.com/us.archive.ubuntu.com/g' /etc/apt/sources.list
```
of course modify the ending for the mint repo stylings.
This line will replace all the lines that have the archive.ubuntu.com line in them.
Then run an update again.

---

### Post by thisisdexter on 2013-12-22
Hi deadflowr,

Boy am I glad you guys exist in this planet! - FAITH IN HUMANITY RESTORED :D :D :D

So I added gb.archive.ubuntu.com and that error went away.

I am still getting error related to 
[B]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner  
[/B]
I just ended up deleting that line, as it made no sense. Do you think I should be bothered by it. As now I am not getting any error at all.

Cheers!

---

### Post by path2 on 2014-01-23
Hi, you may find a **"Ubuntu Sources.list Generator"** according to location and preferences:
 [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
Here is an example that worked fine with a new fresh install of Linux Mint 16 Petra in **/etc/apt/sources.list.d/official-package-repositories.list**
Usual command after changing the source.list is: **sudo apt-get update**


###### Ubuntu Main Repos
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) saucy main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) saucy-security main restricted universe multiverse 
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) saucy-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner

Peace & Blessings

---

