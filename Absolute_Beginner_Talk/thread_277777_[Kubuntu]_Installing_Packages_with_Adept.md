---
title: "[Kubuntu] Installing Packages with Adept"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by b4d0m3n on 2006-10-15
Right. Consider me a complete newbie to Linux and Ubuntu/Kubuntu. Okay? Cool. Now, let's say I want to install Firefox or Opera on my Kubuntu PC. What do I do? I'm confused, and guides don't seem to be helping, just confusing me more. Can someone assist me with this?

---

### Post by steve.horsley on 2006-10-15
Far and away the easiest way to install software is to look for the Ubuntu package for it. Applications->Add/Remove i think. Or if you know the package name, System->Administration->Synaptic package manager. 

If you choose to download software from elsewhere, you really need to follow their instructions, as different people package software in different ways. The two most popular are just to ship a binary tarball (.tar.gz) that you unzip into a directory somewhere, or a source tarball (.tar.gz) that you unzip and then compile. Some people provide a .deb file that you can just double-click to install.

Firefox (from Mozilla) comes as a binary tarball. Unzip it and then (as root) copy the extracted firefox directory to somewhere like /opt. Then you can start it with the command /opt/firefox/firefox. You can change the firefox link in /usr/bin to point to this new version if you want (I do).

---

### Post by TheWizzard on 2006-10-15
> What do I do? I'm confused, and guides don't seem to be helping, just confusing me more. 

it is very simple, but very different from windows. 
most ubuntu software is in deb-packages (the equivalent of setup.exe). these can be found on websites, called repositories (the equivalent of download.com & tucows.com). you can go there and find the software you want, but this is not ideal. 
therefore, smart people developed programms like apt (advanced packaging tool) to automate the web-searching stuff.
if you want to install firefox, you just need to open the terminal and type:
```
sudo apt-get **install** firefox
```
that's all you have to do to install firefox! 
sorry bout my mistake :oops: 

now, some people don't like the command line. therefore graphical interfaces for apt were developed. adept is such a graphical interface. to install firefox, you just open adept, type your password if adept asks you to, and type firefox in the search field. if you find your firefox package, click "request install" and then "apply changes". 

this is the simplified story. does this help? 
for more information, see: 
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

---

### Post by b4d0m3n on 2006-10-15
Thanks, guys. Both of your answers go a long way to helping me understand what in the heck I'm doing, but I still have the following issues:

Moving an Unzipped Firefox folder to opt - Apparently I'm not root, and I have no idea how to change file permissions. Also,

sudo apt-get firefox gives me

E: Invalid operation firefox.

---

### Post by xpod on 2006-10-15
You might need to enable extra`s repositries if you`ve just set up

This site is great for starters

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Arby on 2006-10-15
You've missed the word install on the commandline version, that's why it doesn't work. Should be ```
sudo apt-get install firefox
```. apt-get expects the first thing it sees to be an operation (eg install or uninstall) so the way you had it apt-get is trying to perform the operation 'firefox'. Obviously this makes no sense. That's what the error message means anyway.

Personally I prefer to use the graphical tool adept. If there isn't a shortcut on your desktop then it's under system on the main menu. When you start this program it should ask you for a password, enter your usual login password. This means you will be running adept as a superuser which should solve your permissions problems. Then as mentioned earlier just search for firefox then choose request install and apply changes.

Hope that helps

Take a deep breath and stick with it, you'll find plenty of help here:)

---

### Post by xpod on 2006-10-15
```
sudo aptitude update
```

and

```
sudo aptitude install firefox
```

Is the best way if using the terminal from what ive gathered so far...
Adept`s even easier though.
You`ll pick it up...ayisu`s sites are great for getting to grips with the basics of it all.
Good for all us psycho`s.......cats or otherwise.

Good luck and enjoy.....you might have some problems pulling yourself away from the thing but with any other issues the folks on here or of course google and docs\wiki`s etc will help solve most things:D

---

### Post by TheWizzard on 2006-10-15
the Unofficial Ubuntu 6.06 (Dapper Drake) Starter Guide is a great place to configure your box and install everything you need: 
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by b4d0m3n on 2006-10-18
Thought I'd update. I left Kubuntu for a few days because I had a ton of work to do, but now I am back to dabble. The sudo apt-get install firefox command now gives me:

Reading package lists... Done
Building dependency tree... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnss3
E: Package firefox has no installation candidate

Right. I have set about enabling extra repositories. I actually gave it a go last time and updates stalled at 0%. I'm looking into this now, and I'll bug you guys with more questions as time goes on. Thanks.

---

### Post by b4d0m3n on 2006-10-18
Actually, alright... um. Following the psychocats tutorial for enabling extra repositories, the damn thing stalls while waiting for headers, then times out. Hm. Any advice?

---

### Post by Arby on 2006-10-18
Give us more information. 
1) Are you doing this through the terminal or using the adept gui?
2)Are you having trouble with psychocats tutorial or with the firefox installation, at what step?
3) Whichever interface you are using, what commands  have you tried and what output are you seeing?

If you are working on the commandline post whaever errors or output you are seeing. If you are using adept and you are seeing the progress bar hang press the show details button and you should see some more verbose output, post that. I have a few suspicions but I'd be guessing blind.

---

### Post by b4d0m3n on 2006-10-18
> **Arby said:**
> Give us more information. 
1) Are you doing this through the terminal or using the adept gui?
2)Are you having trouble with psychocats tutorial or with the firefox installation, at what step?
3) Whichever interface you are using, what commands  have you tried and what output are you seeing?

If you are working on the commandline post whaever errors or output you are seeing. If you are using adept and you are seeing the progress bar hang press the show details button and you should see some more verbose output, post that. I have a few suspicions but I'd be guessing blind.

Right. Well, right at this moment I'm trying to fudge around with the terminal and adept. I think. This is what I get after I type in

> sudo aptitude update

I get:

> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done

And after editing the sources to include:

> ## Uncomment the following two lines to fetch updated software from the network
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted 
 ## Uncomment the following two lines to fetch major bug fix updates produced
 ## after the final release of the distribution.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted 
 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse 
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main 
 deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
 deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free

Now I'm confused. Heh. :)

Is this enough info? I'm a complete newbie at this. It takes a heck of a lot to get me thinking around these issues.

---

### Post by Arby on 2006-10-18
Yes it is daunting at first but it gets easier and quicker with time. You're doing things the right way so just stick with it:) 

OK, I'm a little slow today, just so I can be clear where we're up to.
Are we following the guide here [http://www.psychocats.net/ubuntu/sources?](http://www.psychocats.net/ubuntu/sources?)

You have followed through, changed your source.list as described there and you're trying to run the last 'sudo aptitude update' command. This is the point that's causing the errors you posted above. Is that correct?

If so there is a suggestion is at the bottom of the linked page. If not where are we up to.

This is just a guess but I wonder if the reason you can't connect is because you're having a problem with the GPG key not authenticating as suggested in the linked guide. In case you don't know a GPG key is something that ubuntu stores on your system so that when you connect to the ubuntu repositories they 'know' that the request is coming from a bona fide ubuntu system and not some malicious individual intent on damage. There is an explanation on the basic concept here [https://help.ubuntu.com/community/SecureApt?highlight=%28keys%29%7C%28GPG%29](https://help.ubuntu.com/community/SecureApt?highlight=%28keys%29%7C%28GPG%29)

Try the solution suggested on psychocats page but I stress I don't know if this will work or not. It's what I'd try but proceed at your own risk:)

---

### Post by b4d0m3n on 2006-10-18
> **Arby said:**
> Yes it is daunting at first but it gets easier and quicker with time. You're doing things the right way so just stick with it:) 

OK, I'm a little slow today, just so I can be clear where we're up to.
Are we following the guide here [http://www.psychocats.net/ubuntu/sources?](http://www.psychocats.net/ubuntu/sources?)

You have followed through, changed your source.list as described there and you're trying to run the last 'sudo aptitude update' command. This is the point that's causing the errors you posted above. Is that correct?

If so there is a suggestion is at the bottom of the linked page. If not where are we up to.

This is just a guess but I wonder if the reason you can't connect is because you're having a problem with the GPG key not authenticating as suggested in the linked guide. In case you don't know a GPG key is something that ubuntu stores on your system so that when you connect to the ubuntu repositories they 'know' that the request is coming from a bona fide ubuntu system and not some malicious individual intent on damage. There is an explanation on the basic concept here [https://help.ubuntu.com/community/SecureApt?highlight=%28keys%29%7C%28GPG%29](https://help.ubuntu.com/community/SecureApt?highlight=%28keys%29%7C%28GPG%29)

Try the solution suggested on psychocats page but I stress I don't know if this will work or not. It's what I'd try but proceed at your own risk:)

Tried the psychocats solution. At typing 

sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list sudo aptitude update

I get:

cp: target `update' is not a directory

I will take a look at GPG key. Is there a way of fixing it?

---

### Post by Arby on 2006-10-18
> **b4d0m3n said:**
> Tried the psychocats solution. At typing 

sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list sudo aptitude update

I get:

cp: target `update' is not a directory

That's because it's meant to be two commands like this
```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list 
sudo aptitude update
``` The first line is a copy command, the last term in a copy command is where you want to copy to so it thinks update is the target.

If it is a key problem I'm hoping psychocats solution will fix it, if not we'll keep trying.

---

### Post by b4d0m3n on 2006-10-18
Hmm. All I get is:

> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done

So... yes. Of course, I could be making some peabrained mistakes. How do we fix this GPG thing, then?

---

### Post by Arby on 2006-10-18
So back where we were before then. OK looks like it maybe wasn't the GPG key problem then, my bad sorry. I'm struggling for ideas now so I'll put the disclaimer in here: I do not know for certain the solution to the problem.

That said I am happy to try and help you work through it if you want to. If anybody does recognise this and knows the answer shout up. 

I did find this by searching these forums
[http://ubuntuforums.org/showthread.php?t=206578&highlight=GPG+authentication+problem](http://ubuntuforums.org/showthread.php?t=206578&highlight=GPG+authentication+problem)
(Note to self do this earlier in future)

This person seems to have had the same problem you are. They traced the problem to their apt.conf file. Editing this fixed their problem so you could try that. See linked thread for instructions and ask if you don't understand what you need to do

---

### Post by b4d0m3n on 2006-10-18
Look, I'm happy to give stuff a go. :) I have time to play around with this, so no sweat there. I'll take a look at the thread tomorrow night, play around and see what I come up with. Getting a tad late for me. :) Thanks for the help so far. I'm glad there's a community for these types of things.

---

### Post by Bachstelze on 2006-10-18
Is your connection working properly ? You seem to have a DNS problem here...

---

### Post by b4d0m3n on 2006-10-18
> **HymnToLife said:**
> Is your connection working properly ? You seem to have a DNS problem here...

Well, I'm posting here. So it seems to be working alright. Other than that, I'm not sure what a DNS problem could constitute.

---

### Post by Bachstelze on 2006-10-18
Basically, the DNS server is the one redirecting you to the correct IP when you type an internet address. Here, you're redirected to 1.0.0.0 whatever host you type, so there's obviously a problem. What if you use apt-get instead of aptitude ?

---

### Post by justin whitaker on 2006-10-18
> **b4d0m3n said:**
> Look, I'm happy to give stuff a go. :) I have time to play around with this, so no sweat there. I'll take a look at the thread tomorrow night, play around and see what I come up with. Getting a tad late for me. :) Thanks for the help so far. I'm glad there's a community for these types of things.

You might want to try seperating Root from SuperUser. Type in sudo passwd, and give Root another password, then try running apt-get via Root. Doesn't seem like it would work, but I had a prior install hang on this until I updated as Root. Could work. *shrug*

---

