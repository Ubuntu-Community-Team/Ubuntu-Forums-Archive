---
title: "[SOLVED] Installing Java SDK - gcc not installed"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by multi-os-guy on 2007-09-06
Hi,

I'm NEW to Ubuntu (but not hopeless IMHO), and am attempting to install the JDK with Netbeans.  I've downloaded these packages:

jre-6u2-linux-i586.bin
jdk-6u2-ea-bin-b02-linux-i586-12_apr_2007.bin

For installing, I decided I'd update the JVM first, and used chmod and then ran the bin file using the ./ parameter before the filename.  When I typed:

java -version

I still get the default (which doesn't include the Scanner class).  So I ran the 'echo' to install it to the PATH.  I still didn't get the correct result from the java -version command, so I looked for other instructions.  I found one which said to run:

sudo update-alternatives --config java

(my computer is not connected to the internet when using Linux)

This also did not update my java virtual machine, and didn't do anything except tell me I only had one JVM, so I decided to modify my jvm file to include the exact path to my installed (i.e. extracted) java directory, which I did, then logged out and back in and it still didn't work.  

Eventually I decided that I'd remove the original Java installation (the original system one) and so went around randomly removing java packages.  Remember at this point that I don't know much about Linux/Ubuntu.  Well now I can't reinstall any of the java programs (they all report broken packages in the dependencies), the system still reports the default JVM wrongly (or rightly, just not what I want), and I haven't dared to try the JDK, except to chmod and extract it.  

Can someone please give me some directions or hit me between the eyes...:D

I'm not scared of installing Linux Ubuntu on a clean install, so if it would be quicker and easier (the only things I've used it for so far is Web Design and Java Programming, and my Java won't compile :) ) I can just go back to a brand new system and come at this fresh...provided some kind person will give me a nudge or pointer.

Thanks and regards,
Daniel

---

### Post by Perfect Storm on 2007-09-06
enable universe and multiverse in your sourcelist, (check here for source-list generator: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) )

Then,

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-plugin

```

Then java sdk is installed, no need to download software from all diffrent places ;)

---

### Post by aitorcalero on 2007-09-06
> **multi-os-guy said:**
> Hi,
(my computer is not connected to the internet when using Linux)


Bad news!!! :o why?

Maybe you need to configure Synaptic to use Ubuntu CDROM instead Ubuntu Repos severs.

---

### Post by SOULRiDER on 2007-09-06
AFAIK Sun's Java isnt on the DVD or the CD.
multi-os-guy, you could browse [http://packages.ubuntu.com](http://packages.ubuntu.com) and fetch the package youself along with its dependencies... but its a lot of work to do manually.

---

### Post by multi-os-guy on 2007-09-06
> **aitorcalero said:**
> Bad news!!! :o why?

Maybe you need to configure Synaptic to use Ubuntu CDROM instead Ubuntu Repos severs.

...so my java SDK is virtually useless to me?  That doesn't sound great.  Might keep fiddling around rather than download a heap more packages individually...surely there MUST be some way to modify the PATH variables to look up my specific 'java' and 'javac' files.  Maybe I'm missing something...does multiverse HAVE to be installed before I can use an external Java package?

I've reformatted my Ubuntu installation and reinstalled, so I haven't got the old issues.  Anyone with instructions or assistance on how to install the Java Development Kit from the downloadable 'bin' files would be appreciated.

Thanks anyway, guys, maybe one day I'll get broadband, but until then...I guess I'll have to keep looking...I think I've researched more in my two months of Ubuntu than I've done in my 3 years of university...and frankly, I just don't have that kind of time.  If someone has a long, complicated, roundabout how-to with spelling mistakes and bad grammar I'll be VERY HAPPY to read it and thank the author just as long as it works!!!  ::sigh::

---

### Post by aitorcalero on 2007-09-06
[http://www.yiluda.net/manual/linux/man/alternatives.html](http://www.yiluda.net/manual/linux/man/alternatives.html)
[http://blog.stevenkroon.com/2006/08/29/debian-update-alternatives/](http://blog.stevenkroon.com/2006/08/29/debian-update-alternatives/)

Hope this helps!

---

### Post by multi-os-guy on 2007-09-06
Thanks for the links, aitorcalero!  I'll hopefully learn something tomorrow morning...OK, this morning...it's 2:15 a.m. here.  Stephen Kroon's site looks very promising.

---

### Post by multi-os-guy on 2007-09-07
Used wrong instructions on first post...

---

### Post by multi-os-guy on 2007-09-07
Well I managed a work-around, and can now compile my programs in Ubuntu.  I don't have an SDK installed as such, but I can use the javac command from the command prompt.

Essentially, what I did was found some instructions elsewhere on how to set up a runtime environment, which worked perfectly, and then I just added my java SDK directory to the PATH for BASH.  Pretty simple, all it required was to edit my /etc/profile file, and add the following at the end of the file:

PATH-/home/daniel/java/jdk1.6.0_2/bin:${PATH}
export PATH
JAVA_HOME=/home/daniel/java/jdk1.6.0_2/bin
export JAVA_HOME

(Please note that I found all the information from elsewhere, not my own testing :) )

This doesn't give me an installed java SDK, but it does allow me to compile, which is all I need, as I'm used to using Notepad++ or Textpad for creating my programs anyway.  I will continue checking to see whether the java-package gets updated to include Java SDK 6, and when it does I'll install Netbeans as well, but until then at least I can still program!!!

The more I learn, the better I'll remember it!  (now I really ought to go and write a tutorial for my website...)

Thanks heaps, people,
Regards,
Daniel

---

