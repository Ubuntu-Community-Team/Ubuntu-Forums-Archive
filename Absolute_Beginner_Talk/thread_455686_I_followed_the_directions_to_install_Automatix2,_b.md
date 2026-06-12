---
title: "I followed the directions to install Automatix2, but it doesn't like me."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-05-26
I used this link to install Automatix2. 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2)

My command line coding for the entire duration of attempting to install each step. Not really sure what else to do. But if anybody can direct me on how to install Frostwire without automatix2, that'd be great. That's all I was getting automatix2 for...






jason@jason:~$ sudo dpkg -i automatix2_1.1-3.10-7.04feisty_i386.deb
Password:
dpkg: error processing automatix2_1.1-3.10-7.04feisty_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 automatix2_1.1-3.10-7.04feisty_i386.deb
jason@jason:~$ sudo dpkg -i automatix2_1.1-3.10-7.04feisty_i386.deb
dpkg: error processing automatix2_1.1-3.10-7.04feisty_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 automatix2_1.1-3.10-7.04feisty_i386.deb
jason@jason:~$ sudo dpkg -i automatix2_1.1-3.10-7.04feisty_i386.deb
dpkg: error processing automatix2_1.1-3.10-7.04feisty_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 automatix2_1.1-3.10-7.04feisty_i386.deb
jason@jason:~$ echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main" | sudo tee -a /etc/apt/sources.list
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
jason@jason:~$ 
jason@jason:~$ echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main" | sudo tee -a /etc/apt/sources.list
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
jason@jason:~$ wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
--21:28:46--  [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
           => `automatix2.key'
Resolving [www.getautomatix.com](www.getautomatix.com)... 216.120.255.9
Connecting to www.getautomatix.com|216.120.255.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,706 (1.7K) [application/pgp-keys]

100%[====================================>] 1,706         --.--K/s             

21:28:48 (102.37 MB/s) - `automatix2.key' saved [1706/1706]

jason@jason:~$ gpg --import automatix2.key
gpg: directory `/home/jason/.gnupg' created
gpg: can't open `/gnupg/options.skel': No such file or directory
gpg: keyring `/home/jason/.gnupg/secring.gpg' created
gpg: keyring `/home/jason/.gnupg/pubring.gpg' created
gpg: /home/jason/.gnupg/trustdb.gpg: trustdb created
gpg: key E23C5FC3: public key "Arnav Ghosh (Automatix Team Lead) <greyrod@gmail.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
jason@jason:~$ gpg --export --armor E23C5FC3 | sudo apt-key add -
OK
jason@jason:~$ sudo aptitude update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                   
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                   
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release [6738B]                        
40% [Connecting to us.archive.ubuntu.com (91.189.88.31)] [Waiting for headers] [
Get:3 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages [9348B]                  
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                  
Get:6 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages [9348B]                  
99% [Waiting for headers] [Waiting for headers] [Connecting to elisa.fluendo.combzip2: (stdin) is not a bzip2 file.
Err [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                            
  Sub-process bzip2 returned an error code (2)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US            
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Ign [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty Release.gpg                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty/main Translation-en_US
Hit [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty Release
Ign [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty/main Packages
Hit [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty/main Packages
Fetched 16.3kB in 1s (13.5kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
jason@jason:~$ 
jason@jason:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                       
Get:4 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages [9348B]                 
99% [4 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fbzip2: (stdin) is not a bzip2 file.
Err [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
  Sub-process bzip2 returned an error code (2)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Get:6 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages [9348B]                 
99% [6 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fbzip2: (stdin) is not a bzip2 file.
Err [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
  Sub-process bzip2 returned an error code (2)
Ign [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release              
Ign [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty/main Translation-en_US                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Hit [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty/main Packages
Hit [http://elisa.fluendo.com](http://elisa.fluendo.com) feisty/main Packages
Fetched 6B in 0s (6B/s)
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
jason@jason:~$ sudo aptitude install automatix2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
jason@jason:~$

---

### Post by BarfBag on 2007-05-26
Dang.  I sure hope you have a backup of your sources.list.  If not, try [Source-O-Matic]("http://www.ubuntu-nl.org/source-o-matic/").  Replace the lines in /etc/apt/sources.list with the lines it spits at you.

Are you using Feisty Fawn?  If so, there's a much easier way to install a .deb which might give you better results.  Just double click on the file.  :D

---

### Post by Roasted on 2007-05-26
Somehow I never noticed that the icon was put on my desktop. Otherwise I would of said duur and just double clicked it to install it. It's installed now. Thanks for the memo, haha.

But why do you say that about my sources.list? I never even changed anything in it, except to add a repository for Elisa media player.

---

### Post by Polygon on 2007-05-27
if you need to restore your old sources.lst, you should have some backups (automatix makes backups before it edits it)
they should be in /etc/apt/ then you should see a bunch of "source.lst backups"

---

### Post by taurus on 2007-05-27
And another one screws up his /etc/apt/sources.list trying to install Automatix2.  Any reason you need Automatix2 since everything that you need is in Add/Remove, synaptic, apt-get, or aptitude.

---

### Post by Roasted on 2007-05-27
> **taurus said:**
> And another one screws up his /etc/apt/sources.list trying to install Automatix2.  Any reason you need Automatix2 since everything that you need is in Add/Remove, synaptic, apt-get, or aptitude.

I'll be honest... it's late, it's my 21st birthday, and I've had quite a few drinks... but I can't seem to understand what you said. Are you saying there's essentially no reason to use automatix since everything that automatix offers is already available by other means? 

If so, I was just having trouble installing frostwire cause I suck and didn't realize I already downloaded the .deb. It was a duur moment. But now I have automatix... and I forget why... I think I'm done for the night...

---

### Post by OrangeCrate on 2007-05-27
> **Roasted said:**
> I'll be honest... it's late, it's my 21st birthday, and I've had quite a few drinks... but I can't seem to understand what you said. Are you saying there's essentially no reason to use automatix since everything that automatix offers is already available by other means? 

If so, I was just having trouble installing frostwire cause I suck and didn't realize I already downloaded the .deb. It was a duur moment. But now I have automatix... and I forget why... I think I'm done for the night...

I don't blame you for calling it a night...

What you experienced in this thread, is an ongoing problem with anyone who, in a few contributor's opinions, is "dumb" enough to use, and therefore to post a question about Automatix.

Though many use the program, including Michael Dell apparently, even though this is the "Absolute Beginner Talk" forum, someone will jump all over you for using Automatix.

You will be better served to tune into Automatix's forum for answers to any questions you might have. You can find it here:

[http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

And no, I personally don't use it, but I understand why people do.

---

### Post by hyper_ch on 2007-05-27
Everything automatix offers can also be achieved with other means and by not using automatix you will even learn more...

---

### Post by carusoswi on 2007-05-27
> **OrangeCrate said:**
> I don't blame you for calling it a night...

What you experienced in this thread, is an ongoing problem with anyone who, in a few contributor's opinions, is "dumb" enough to use, and therefore to post a question about Automatix.

Though many use the program, including Michael Dell apparently, even though this is the "Absolute Beginner Talk" forum, someone will jump all over you for using Automatix.

You will be better served to tune into Automatix's forum for answers to any questions you might have. You can find it here:

[http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

And no, I personally don't use it, but I understand why people do.

I will throw in a vote FOR automatix.  I use it, and find it very simple and efficient at installing packages that it downloads for me.  It has never broken my machine, and, I'm guessing that any machines it has "broken" probably had some sort of errors on them that caused the error, or the package was incompatible or something.

I do not understand how some see the need to put that program down.  If ever it was broken, my guess is that the developers have been working hard to improve it.  I certainly appreciate the simple way that it takes over the install process, and, while I enjoy learning about Linux and its terminal commands, I like playing with new software more, and Automatix has greatly increased the speed at which, when I have a need to rebuild my Ubuntu installation, I can quickly go out and find those few programs that I find essential and install them without a great deal of fuss (NDIS Wrapper, NTFS read/write, Crossover, etc).  I know I can do all of that without Automatix - Crossover is as simple as downloading the program and letting Synaptics take over.

But, Automatix works, is fast, most of the programs I need are right there in the Automatix list of applications.

For those that are comfortable installing applications without Automatix, wonderful . . . I just don't think it is in the spirit of the ubuntu community for someone to respond to a post for help (with any application - not just Automatix) with a flame of the program.

My 2-cents.

Caruso

---

### Post by oilchangeguy on 2007-05-27
please explain WHY you would use a command to install automatix??????? they do have a web site!
try this:[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb)

---

### Post by Roasted on 2007-05-27
Again, when I was trying to install everything I had a few drinks and didn't really know what I was doing.

I downloaded automatix only to install frostwire. I had trouble installing frostwire for some reason, and I tried to do it the manual way. I got the icon, but next to the icon the little blue globe wasn't there. Then when I clicked on it it wouldn't load frostwire... so I resorted to automatix.

Everything else I installed on my own from the Feisty Fawn Guide though. :) I just needed a last resort to get frostwire asap to get a song for my buddy.

---

### Post by dptxp on 2007-05-27
I have vowed not to touch Compiz, Beryl, Automatix, Easybuntu or Edubuntu.

I love to have clean installations.

Ciorrection - I meant medibuntu, not edubuntu.

---

### Post by Polygon on 2007-05-27
> **dptxp said:**
> I have vowed not to touch Compiz, Beryl, Automatix, Easybuntu or Edubuntu.

I love to have clean installations.

edubuntu?

umm thats another distro... like xubuntu...kubuntu... etc

---

### Post by arnieboy on 2007-05-27
> **Roasted said:**
> I used this link to install Automatix2. 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2)


That is not the official website of Automatix.. you have tried too many things which has resulted in this mess. 
Paste the results of the following command:
```
cat /etc/apt/sources.list
```

---

### Post by arnieboy on 2007-05-27
> **taurus said:**
>  Any reason you need Automatix2 since everything that you need is in Add/Remove, synaptic, apt-get, or aptitude.

You seem to very confident about what you are saying.. I only wish you were a little better-informed. Would you mind dropping by in #automatix on irc.freenode.net to discuss how Automatix really works with Automatix devs? I am saying this because I see you making a deliberate negative comment about Automatix in every support thread which does nothing but spread ill-will. If you discuss with us, we could drive away some of your wrong notions. 

-Arnie
Team Lead
Automatix

---

### Post by ryanVickers on 2007-05-27
I made a simple guide to install automatix2 really easlly [here]("http://ubuntuforums.org/showthread.php?t=455753").  there's a bunvh of arguing and complaining/discussions going on, but just but just red the first post and continue with the link.  It should work fine.

---

### Post by hyper_ch on 2007-05-27
Well Arnie

I can't think of anything not to be easily installed that is offered by automatix...

---

### Post by arnieboy on 2007-05-27
> **hyper_ch said:**
> Well Arnie

I can't think of anything not to be easily installed that is offered by automatix...
Ease and difficulty are extremely relative terms.. whats difficult to you might be a bag of peanuts to me. 
We do not try to sell ourselves as the easiest package installer on this planet... We are simply there.. people use our software, like it and recommend it to others.. thats it.  
You are very welcome to tell people to do everything manually or even compile an OS from scratch. 
Nobody in the Automatix team has or should have a problem with that.

---

### Post by Roasted on 2007-05-28
jason@jason:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
jason@jason:~$

---

### Post by Foaming Draught on 2007-05-29
I used Automatix when it first became available, and found it invaluable for the new Linux user which I was.   For a few Ubuntu distributions I didn't use it because I wanted to master the Synaptic GUI and apt-get command line.  Now I've used it again on Feisty, not least because a lot of thought has gone into which packages to include.  So I browse through the Automatix2 GUI, see a package which I hadn't thought of (nor perhaps had even heard of), read its description and say to myself, "Hey, I'll tick that, it'll be cool."

I love Ubuntu so much that I want the whole world to take it up.  That will only happen if we have ease-of-use tools like Automatix, and I'm dead grateful to arnieboy and his team.

It's never given me a moment's trouble.

---

### Post by arnieboy on 2007-05-29
> **Roasted said:**
> jason@jason:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
jason@jason:~$
you have two copies of the automatix repository which is causing this issue (look just above  **#AUTOMATIX REPOS START** ). Delete **one of the following 2 lines** from your /etc/apt/sources.list:
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
and do a
```
sudo apt-get update
sudo apt-get remove automatix2
sudo apt-get clean
sudo apt-get install automatix2
```
and then everything will be fine.

---

