---
title: "No virus definitions found!"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-12-14
after a fresh install i installed clamtk but when i run in it i get the following message:
"Warning: No virus definitions found! If you are sure you have definitions installed, please inform the developer where your definitions are held so the paths can be added."

except this everything else on it seems to be ok..
any ideas?

---

### Post by skyjacker on 2007-12-14
> **someoneouthere said:**
> after a fresh install i installed clamtk but when i run in it i get the following message:
"Warning: No virus definitions found! If you are sure you have definitions installed, please inform the developer where your definitions are held so the paths can be added."

except this everything else on it seems to be ok..
any ideas?You need to install and run "clamfresh" It's in the repos.

---

### Post by someoneouthere on 2007-12-14
no clamfresh found in the repos...

---

### Post by someoneouthere on 2007-12-14
maybe it has another name

---

### Post by disturbedite on 2007-12-14
you know you don't really need an anti-virus program on linux right?  prolly except in rare circumstances.

---

### Post by Dave Otter on 2007-12-14
go to  System Admin-Synaptic  
                                           install clamav-getfiles
                                                         clamav freshclam

---

### Post by someoneouthere on 2007-12-14
well i know... 
but it gives you a feeling of safety....lol
just in case those circumstances come

---

### Post by Dave Otter on 2007-12-14
go to System Admin-Synaptic
install clamav-getfiles
clamav freshclam
__

---

### Post by someoneouthere on 2007-12-14
found it: just had to reinstall freshclam...
:) thank a lot

---

### Post by aysiu on 2007-12-14
> **someoneouthere said:**
> well i know... 
but it gives you a feeling of safety....lol
just in case those circumstances come
That feeling is a false sense of security, then.

If a new threat were to come out, having anti-virus installed wouldn't immediately prevent the threat from being dangerous to your computer. The threat would arrive and cause havoc first. Then the definitions would have to be updated after the anti-virus maintainers figured out how to stop the threat, and then you'd get protection after the fact.

I guarantee you I can install anti-virus faster than the anti-virus maintainers can update the definitions for a newly discovered threat.

---

### Post by Perfect Storm on 2007-12-14
The anti-virus applications for linux is set for discovering windows virus - so how much use it then :KS

---

### Post by someoneouthere on 2007-12-14
> **aysiu said:**
> That feeling is a false sense of security, then.

If a new threat were to come out, having anti-virus installed wouldn't immediately prevent the threat from being dangerous to your computer. The threat would arrive and cause havoc first. Then the definitions would have to be updated after the anti-virus maintainers figured out how to stop the threat, and then you'd get protection after the fact.



i agree.
but what about the existing definitions?

---

### Post by aysiu on 2007-12-14
> **someoneouthere said:**
> i agree.
but what about the existing definitions?
What about them?

The most viable security threats to Linux right now are weak passwords and malicious users tricking others into entering dangerous code in the terminal.

---

### Post by thelatinist on 2007-12-14
> **someoneouthere said:**
> i agree.
but what about the existing definitions?

That's just the point: those existing definitions aren't going to do anything to increase the security of your system because there is not existing threat for them to protect you against! Those virus definitions you're so gung-ho about installing are to scan for Windows viruses that won't even run on your system.

---

### Post by pdlethbridge on 2007-12-14
We are interested in protecting ourselves from windows virus's but do we really need clam av if we don't have windows on our computer? How about wine or wine doors, would they help us get virus's?

---

### Post by aysiu on 2007-12-14
> **pdlethbridge said:**
> We are interested in protecting ourselves from windows virus's but do we really need clam av if we don't have windows on our computer? How about wine or wine doors, would they help us get virus's?
Unless you are running Linux as a mail server, there's no need for you to run Clam AV.

---

### Post by thelatinist on 2007-12-14
> **pdlethbridge said:**
> We are interested in protecting ourselves from windows virus's but do we really need clam av if we don't have windows on our computer? How about wine or wine doors, would they help us get virus's?

No.  Even if you did manage to get a windows virus to run under Wine (someone tried with several viruses a while back and it was no mean feat to get one to do so...and even then it didn't actually do what it was designed to do), it couldn't touch your system.  You're stuck in the old Windows way of thinking where an OS needs to be filled with bloatware to give it some semblance of 'security.'  Linux is secure by design.

---

### Post by someoneouthere on 2007-12-15
Confirmed.... thanks:KS

---

### Post by disturbedite on 2007-12-15
actually, i think i remember reading that viruses can hose wine, so that you have to reinstall it, but of course that depends on each individual circumstance.  but of course the "virus" caused no damage whatsoever to the (linux) system, for obvious reasons.

---

### Post by dcstar on 2007-12-15
> **aysiu said:**
> Unless you are running Linux as a mail server, there's no need for you to run Clam AV.

Maybe, but I run it and have my Evolution set up to use it to scan all my incoming e-mails.

It regularly identifies various "Phishing" e-mails (that get past Bogofilter) and warns me about them, so it still does have value in the Linux environment.

---

### Post by adn258 on 2008-01-29
> **Dave Otter said:**
> go to System Admin-Synaptic
install clamav-getfiles
clamav freshclam
__

I am having the SAME problem this guy stated at the top and reinstalling it didn't help for me does anyone have any suggestions.

---

### Post by Endolith on 2008-02-08
> **disturbedite said:**
> you know you don't really need an anti-virus program on linux right?

False sense of security?

---

### Post by aysiu on 2008-02-08
> **Endolith said:**
> False sense of security?
That's exactly what running anti-virus gives you.

---

### Post by Endolith on 2008-02-08
> **aysiu said:**
> That's exactly what running anti-virus gives you.

So I shouldn't run an anti-virus program if I'm downloading files from dubious sources that will be used on a Windows machine?  :)

Telling newbs that they don't have to worry about security at all because "Linux is safe by design" gives them a false sense of security.  Look at [https://help.ubuntu.com/community/UnsafeDefaults](https://help.ubuntu.com/community/UnsafeDefaults) for examples of some things that are less than 100% safe.



Anyway, I just installed clamtk from the Add/Remove option (why doesn't Synaptic show popularity?) and it's giving me the same error:

> Warning: No virus definitions found! If you are sure you have definitions installed, please inform the developer where your definitions are held so the paths can be added.

When I run sudo freshclam I get:

> ClamAV update process started at Fri Feb  8 00:20:06 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.91.2 Recommended version: 0.92
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
daily.cvd is up to date (version: 5733, sigs: 37569, f-level: 21, builder: ccordes)


And clamtk still gives the same error.  What do I do?

Also, isn't freshclam supposed to be automatic?

---

### Post by aysiu on 2008-02-08
> **Endolith said:**
> So I shouldn't run an anti-virus program if I'm downloading files from dubious sources that will be used on a Windows machine? I never said that. I said you don't need to run anti-virus on Linux, and running it on Linux could give you a false sense of security. If you're using a Windows machine, that's an entirely different story.

> Telling newbs that they don't have to worry about security at all because "Linux is safe by design" gives them a false sense of security.  Look at [https://help.ubuntu.com/community/UnsafeDefaults](https://help.ubuntu.com/community/UnsafeDefaults) for examples of some things that are less than 100% safe. Again, I never said that. I didn't say people don't need to worry about security at all. All I'm saying is that anti-virus on Linux doesn't offer you any security. Read more here:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

By the way, you should read the very top of the page you linked to: > While Ubuntu comes secure and ready to use, many people decide to offer other services on their computer, such as running a FTP server or Apache. The purpose of this page is to advise these users on the settings that they should probably change. If you're running services like that, you'd better know what you're doing. Ubuntu, by default, does not run those services.

---

### Post by Victormd on 2008-02-08
> **aysiu said:**
> That's exactly what running anti-virus gives you.

First off, I don't have an anti-virus on my Ubuntu system I blindly (maybe erroneously) believe in the Linux security. However, I can't say the same for Windows.

As for the "false sense of security," I would have to disagree. Under any system, if there is a threat (past and present) and an anti-virus is capable of detecting that threat and eliminating it, then it's a true sense of security. Looking into the future, lets say a threat came out and affected 10% of the computers (don't know how realistic the 10% is but that's irrelevant) before it affects the remaining 90%, an updated virus definition is made available (there are people making money off of this - not in linux case of course) and the 90% who were not affected, update and are "safe" again... then it's a true sense of security for the majority of the users... Not everything is 100%!
... just a thought... :)

---

### Post by Perfect Storm on 2008-02-08
Anti-virus applications are retro-active, so if a new virus is aimed at Ubuntu an anti-virus application won't help you. Note I said Ubuntu and not linux because each distro have a specific setup and so on which makes it very very _very_ hard to make an virus that will infect the entire Linux OS.

The known virus' to Linux have been patched eons ago and are no threat. If a new virus shows up, the system will be patched before you know it - Linux is known for fast updating and patching.

1. Ubuntu comes with port closed, so Ubuntu is secure by default.
2. Use only official sources and trustworthy sources for applications/games/libs 
3. Don't run stuff as admin 


What people have to do(or learn) is to drop the windows mentality. It's one of the hardest thing to do I know. But linux is way diffrent than windows.

---

### Post by hyper_ch on 2008-02-08
> **Artificial Intelligence said:**
> 1. Ubuntu comes with port closed, so Ubuntu is secure by default.
Ports are not closed by default. There's just no service listening to them.

---

### Post by Perfect Storm on 2008-02-08
sorry, my fault.

---

### Post by hyper_ch on 2008-02-08
> **Artificial Intelligence said:**
> sorry, my fault.

I thought so also until this in this forum I was told hundreds of times otherwise ;)

One could however argue that if no application is listening to a port whether it can be called "closed" also in a less formal sense.

---

### Post by tenjin1 on 2008-04-12
I have just recently used Clam AV in Ubuntu to scan a directory with exe Windows program files I got from a questionable place on the net. I wanted to be sure there wasn't any virus or anything malicious in this directory before burning them to cd and giving them to a Windows user to use. Too lazy to boot into windows to perform this task...since I am a constant Ubuntu user.

...so yea, Clam AV can be useful at times in Linux. :)

---

### Post by Endolith on 2008-04-13
> **tenjin1 said:**
> I have just recently used Clam AV in Ubuntu to scan a directory with exe Windows program files I got from a questionable place on the net. I wanted to be sure there wasn't any virus or anything malicious in this directory before burning them to cd and giving them to a Windows user to use. Too lazy to boot into windows to perform this task...since I am a constant Ubuntu user.

...so yea, Clam AV can be useful at times in Linux. :)

Exactly why I want to get mine working.  :)

---

### Post by tenjin1 on 2008-04-13
> **Endolith said:**
> Exactly why I want to get mine working.  :)

I don't use ClamTK, I use ClamAV from the command line so I don't know how to get that working but from what you posted your virus definitons are up-to-date as you posted below:
```
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
daily.cvd is up to date (version: 5733, sigs: 37569, f-level: 21, builder: ccordes)
```
It's just saying your version is 0.91 and the newest is version 0.92.

To scan a directory from command line:
open up a terminal and type:
```
sudo clamscan -r -i /name/of/the/directory/you/want/to/scan 
```
To remove files infected with viruses:
You can add ```
--remove
``` to the clamscan commandline. 

If you want to use the latest version 0.92 you have to download [URL="http://sourceforge.net/project/downloading.php?groupname=clamav&filename=clamav-0.92.1.tar.gz&use_mirror=superb-east"]here
[/URL] but is suggested to remove all other versions first.
Then compile it from source by command line:
```
cd  /to/the/download/directory
```
then once in the download directory, extract the file:
```
tar -zxvf clamav-0.92.1.tar.gz
```
..or right-click-extract

then cd into the folder extracted and compile it by:
```
./configure
sudo make
sudo make install
```

**NOTE** If you are still getting:
```
ERROR: Please edit the example config file /usr/local/etc/clamd.conf.
ERROR: Can't open/parse the config file /usr/local/etc/clamd.conf
```
then you have to comment a line in that config file
```
sudo gedit /usr/local/etc/clamd.conf
```
The first line when you open up the clamd.conf file is this line:
```
# Comment or remove the line below.

Example
```
Until that line is commented out (or removed), you will continue to get that error and clamd will not start, so remove that line. or make it look like:
```
#Example
```

You may also have to do the same thing to the /usr/local/etc/freshclam.conf

Then update clamav by:
```
sudo freshclam
```

---

