---
title: "Can't upgrade to Ubuntu Studio"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Mrich1976 on 2007-05-21
Ok, this is probably a very silly question.

I'm having difficulty upgrading to Ubuntu Studio. I log in, go to Update Manager, it tells me that 7.04 (studio) is available, and I click update. Then it loads a screen (I forget which) and then it tells me that it can't find two files from the web ([http://archive](http://archive)... files) and they have a .gz extension.

I really want to upgrade. I tried to burn a CD at work today, but it's if you're converting from Windows to Ubuntu. If I had one that I could do that was in a Linux format that would be great, but I don't, and my Linux box only has a CD drive, not a DVD drive.

Any help would be very appreciated.

---

### Post by Terl on 2007-05-21
Just to clarify, what version are you using right now?

---

### Post by Mrich1976 on 2007-05-21
Right now, I'm using Edgy Eft (6.10). Although when the update process finished, it gave me an error message (sorry, I didn't write it down) and told me the system may not be stable. So I rebooted, and tried to do the update to Studio.

---

### Post by Terl on 2007-05-21
The upgrade from 6.10 would be to Feisty Fawn not Ubuntu Studio.  If you want Ubuntu Studio you would be better off downloading it and doing a clean install.  The other way is to upgrade to Feisty from 6.10 and then download the other pieces from synaptic.

I would recommend, if you really want studio to download and install clean.  It could be easier in the long run.  Sometimes upgrading is not as smooth as one would hope.

---

### Post by Mrich1976 on 2007-05-21
I burned a CD of Studio, but it's one for if you're converting from Windows to Ubuntu, so it won't work in my CD drive. As I stated earlier, my Linux computer doesn't have a DVD, so if there's a way I can download a version that will work on Linux, and will fit on a CD, that's what I'd need. If you know, could you point me the right way?

Thanks for all your assistance.

---

### Post by Terl on 2007-05-22
> I burned a CD of Studio, but it's one for if you're converting from Windows to Ubuntu, so it won't work in my CD drive.

I assume this means you downloaded the iso for the full Ubuntu Studio, which I show as being > 800 MB.  This is the full distribution for an install.  It is what I recommend you should get, if you could get someone to burn it for you.

PLAN A:  One method I can see for you to do this without burning a dvd is to first upgrade to Ubuntu 7.04 Fesity Fawn.  After that upgrade is complete go to: [This page]("http://ubuntustudio.org/downloads") at Ubuntu Studio and add the repository as shown in the bottom half of the page.  This will add their repository to your synaptic.  When you are done with that, install the packages they list on the page and you are all set.  This should work just fine as long as the upgrade to Feisty Fawn goes well. 

PLAN B:   If upgrade does not work, download Feisty Fawn and burn it to cd (that will fit on a cd).  Do a fresh install from that cd.  Now you have 7.04 on your pc.  Update it, get your graphics drivers installed and then add the repositories as shown above for Ubuntu Studio.  Download all the extra pieces and you are all set.

PLAN C:  [Sorry, scratch plan c, I just reread your post and you have no dvd]  You can buy a copy and have it mailed to you.  Here is one spot:  [Linux Store]("http://www.thelinuxstore.ca/index.php?main_page=advanced_search_result&search_in_description=1&keyword=ubuntu+studio").  This would allow you a clean install of Ubuntu Studio with no extra work.

---

### Post by Mrich1976 on 2007-05-22
Ok, it looks like I'm not communicating clearly. Forgive me, I'm still new to the Linux world. I should know how to do these posts, as I work as a web programmer.

Anyway, What I did was go to the Ubuntu page (not the Studio page) and downloaded the Feisty Fawn (7.04) Desktop Edition. This is the one I burned to CD. That's the one that doesn't work. I did not burn the .iso, I burned the full file structure.

I did this because I was getting errors trying to do the upgrade via Update Manager. I double-checked to ensure that I'm running 6.10 (before the upgrade to 7.04).

So I open the Update Manager, and it tells me a new release (7.04) is available. I click on Upgrade, click through the release notes, and it starts downloading the upgrade tool (after I enter my password). Then I get an error dialog box ("Error During Update").

Here is the error description:

A problem occurred during the update. This is usually some sort of network problem. Please check your network connection and retry.

I know my network is working correctly because I can browse the web and download other updates.

Here is the error I was getting:

Failed to fetch: [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz)

Is there any way to fix that through the terminal? I tried pasting the URL in a browser in my Windows box, and the file is definitely at the URL above.

---

### Post by Terl on 2007-05-22
Thanks for adding the extra information.  Believe me, I understand how difficult it can be to say something the right way!  I see where we are now, and I think we can fix this easily.

I think the following code (I found it at Ubuntu Studio site - link is above this post, says "This page") should fix it up.  It will add the lines you need for synaptic.  It is two separate commands.

```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update 

```

To see it all go:  [Ubuntu Studio]("http://ubuntustudio.org/downloads").  They explain the code I just pasted above.  This should make sure the repositoreis you need are in your synaptic.  After you run the commands, you should be able to get the packages you need.

---

### Post by Mrich1976 on 2007-05-22
I've actually done that, and I got a couple of 404's. I'll go back and do it again tonight, so I can post the exact 404's I'm getting.

When I do the first command, nothing is output to the console, and it just returns me to the prompt. Then when I do the other command I get the 404's.

Thanks again for all your help, and for your patience.

---

### Post by ThinkBuntu on 2007-05-22
For all intents and purposes, you can easily convert 7.04 into Studio 7.04. Took me very little time to convert mine.

---

### Post by Mrich1976 on 2007-05-22
Yes, I understand that, but the problem I'm having is going from 6.10 --> 7.04.

---

### Post by Mrich1976 on 2007-05-22
Alright I ran both commands as suggested in the previous post, and got the following:

OK
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) fiesty Release.gpg
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) fiesty/main Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) fiesty/main Translation-en_US
Get:1 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) fiesty Release
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) fiesty/main Packages
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) fiesty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) fiesty/main Packages
  404 Not Found
Err [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) fiesty/main Packages
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Fetched 4B in 1s (2B/s)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/fiesty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/fiesty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/fiesty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/fiesty/main/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by interglossa on 2007-05-23
When you talk about converting 7.04 to Studio 7.04, does that mean that the 800MB
Ubuntu Studio iso image is really 7.04 with the studio components included?  I have burned a copy of both the 7.04 CD and the Studio DVD.  That would mean there is no point in 'installing' the Studio DVD if I have already upgraded to Fawn.

I have been mulling this over as I see a lot of people complaining about audio in Fawn but on the other hand I have an AC97 on motherboard so it may be a more common and more supported configuration than the systems where people have had problems.

Ubuntu Studio does sound very interesting.  I am surprised it does not have its own forum by now...

---

### Post by moodly45 on 2007-05-30
I'm having a similar problem, trying to upgrade to studio from feisty fawn 7.04. heres what i get:
```
Get: 1 http://gb.archive.ubuntu.com feisty Release.gpg [191B]
Hit http://gb.archive.ubuntu.com feisty/main Translation-en_GB                
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB          
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB
Get: 2 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB        
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/multiverse Translation-en_GB
Get: 3 http://gb.archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://gb.archive.ubuntu.com feisty-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-security/restricted Translation-en_GB 
Ign http://gb.archive.ubuntu.com feisty-security/universe Translation-en_GB   
Ign http://gb.archive.ubuntu.com feisty-security/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com feisty Release             
Hit http://gb.archive.ubuntu.com feisty-updates Release     
Hit http://gb.archive.ubuntu.com feisty-security Release    
Hit http://gb.archive.ubuntu.com feisty/main Packages                         
Hit http://gb.archive.ubuntu.com feisty/restricted Packages                   
Hit http://gb.archive.ubuntu.com feisty/universe Packages                     
Hit http://gb.archive.ubuntu.com feisty/multiverse Packages                   
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com feisty-updates/universe Packages
Hit http://gb.archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com feisty-security/main Packages
Hit http://gb.archive.ubuntu.com feisty-security/restricted Packages
Hit http://gb.archive.ubuntu.com feisty-security/universe Packages
Hit http://gb.archive.ubuntu.com feisty-security/multiverse Packages
Ign http://archive.ubuntustudio.org feisty Release.gpg
Ign http://archive.ubuntustudio.org feisty/main Translation-en_GB
Ign http://archive.ubuntustudio.org feisty/main Translation-en_GB
Get: 4 http://archive.ubuntustudio.org feisty Release.gpg [189B]
Ign http://archive.ubuntustudio.org feisty/main Translation-en_GB
Ign http://archive.ubuntustudio.org feisty/main Translation-en_GB
Ign http://archive.ubuntustudio.org feisty/main Translation-en_GB
Ign http://archive.ubuntustudio.org feisty/main Translation-en_GB
Ign http://archive.ubuntustudio.org feisty Release
Hit http://archive.ubuntustudio.org feisty Release
Ign http://archive.ubuntustudio.org feisty/main Packages
Ign http://archive.ubuntustudio.org feisty/main Packages
Hit http://archive.ubuntustudio.org feisty/main Packages
Hit http://archive.ubuntustudio.org feisty/main Packages
Hit http://archive.ubuntustudio.org feisty/main Packages
Hit http://archive.ubuntustudio.org feisty/main Packages
Err http://archive.ubuntustudio.org feisty/main Packages
  404 Not Found
Err http://archive.ubuntustudio.org feisty/main Packages
  404 Not Found
Fetched 4B in 1s (3B/s)
Failed to fetch http://archive.ubuntustudio.org/dists/feisty/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntustudio.org/dists/feisty/main/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I assume the repository must be wrong? ([http://archive.ubuntustudio.org/dists/feisty/main/](http://archive.ubuntustudio.org/dists/feisty/main/))

---

### Post by moodly45 on 2007-05-31
Sorted it!  just use the script attached!  type: sh ubuntustudio-upgrade-feisty.sh 
into terminal!

---

