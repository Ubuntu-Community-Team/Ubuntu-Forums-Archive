---
title: "Update  and/ or some other problem...please take a look!"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by kristalsoldier on 2007-03-01
When I do the sudo apt-get update command in the terminal, I get the following:

~$ gksudo gedit /etc/apt/sources.list

(gedit:8003): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release.gpg                                   
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release.gpg                          
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Translation-en_US               
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release                              
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [63.2kB]           
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
99% [2 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fobzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
  Sub-process bzip2 returned an error code (2)
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [12.8kB]            
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources [937B]        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [3432B]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [63.2kB]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                        
99% [7 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fobzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
  Sub-process bzip2 returned an error code (2)
Hit [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release                             
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Translation-en_US                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                    
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources              
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages
Hit [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages
Hit [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages
Get:10 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
Fetched 17.2kB in 12s (1422B/s)                                                 
Reading package lists... Done
[COLOR="Red"]W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
manav@manav-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory[/COLOR]

[COLOR="Black"][/COLOR]

I thought I fixed the problem, but now there seems to be more! Please advise!

Thanks

---

### Post by mahy on 2007-03-01
How about posting your /etc/apt/sources.list?

---

### Post by Kateikyoushi on 2007-03-01
To do so copy this to the terminal.

```
cat /etc/apt/sources.list
```

What you should do is check the file and remove duplicated entries.

```
sudo nano /etc/apt/sources.list
```

---

### Post by kristalsoldier on 2007-03-01
Err....I must be doing something wrong...I cut and pasted the command and the result is...

bash: /etc/apt/sources.list: Permission denied

---

### Post by kristalsoldier on 2007-03-01
This is the result of the first command...

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe



deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe

deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all

---

### Post by kristalsoldier on 2007-03-01
And this is the response from the second command...

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

---

### Post by mahy on 2007-03-01
you've got duplicate lines, don't you see? Some of those containing [http://archive.ubuntu.com](http://archive.ubuntu.com) and [http://security.ubuntu.com](http://security.ubuntu.com) are duplicate. Fix it and you'd be ok.

---

### Post by kristalsoldier on 2007-03-01
You mean in the list generated by the second command...yes?

---

### Post by mahy on 2007-03-01
> **kristalsoldier said:**
> You mean in the list generated by the second command...yes?

No. The list is stored in the file /etc/apt/sources.list. 'cat' is the command here used to print that file to the monitor. 'nano' is the name of a commandline text editor. Is it clear? ;)

Just edit that file (however you wish) to remove that duplicate lines.

---

### Post by kristalsoldier on 2007-03-01
OK. So, I put a # in front of either [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US (as an example) or the line which reads [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US  (again as an example).

Yes...I note with appreciate the corrective...:)

---

### Post by mahy on 2007-03-01
> **kristalsoldier said:**
> OK. So, I put a # in front of either [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US (as an example) or the line which reads [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US  (again as an example).

Yes...I note with appreciate the corrective...:)

I don't get it. There's no "Translation-en_US" in the /etc/apt/sources.list file!! That's what you need to edit. But yes, the commenting out is done by putting # to the beginning of a line.

---

### Post by Kateikyoushi on 2007-03-01
Do not look for the endings just for the server and uncomment the duplicated one.
Of course if you would copy paste it here we could do it for you.

---

### Post by picpak on 2007-03-01
I don't get it, from what I see there are no duplicates in that file. deb and deb-src are two different things.

I've had this problem for weeks; I just live with it.

---

### Post by Kateikyoushi on 2007-03-01
Picpak is right I mistook it.

---

### Post by picpak on 2007-03-01
Those are edgy and edgy-updates, two different repos.

---

### Post by kristalsoldier on 2007-03-01
Folks, I am now totally lost! Please...is this critical? Does not seem to be so...the only thing is I can't seem to download certain packages via Synaptic...give me the duplicate error...was fixed last night...but today is another thing.

---

### Post by kristalsoldier on 2007-03-01
> **kristalsoldier said:**
> Folks, I am now totally lost! Please...is this critical? Does not seem to be so...the only thing is I can't seem to download certain packages via Synaptic...give me the duplicate error...was fixed last night...but today is another thing.

So, when try the Synaptic, I get the following errors, which I is the same in the first post...

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages)

---

### Post by kristalsoldier on 2007-03-01
Is there a way to clean out the original source list and create a new one? Is it necessary? Indeed, is it wise to do so?

Thanks

---

### Post by Kateikyoushi on 2007-03-01
You can find sources.lists on this page [LINK]("http://www.psychocats.net/ubuntu/sources") select the right version for yourself, copy paste it into the list.

Then do an update.

```
sudo aptitude update
```

---

### Post by kristalsoldier on 2007-03-01
Thanks

---

### Post by kristalsoldier on 2007-03-01
> **Kateikyoushi said:**
> You can find sources.lists on this page [LINK]("http://www.psychocats.net/ubuntu/sources") select the right version for yourself, copy paste it into the list.

Then do an update.

```
sudo aptitude update
```

I have no idea how this happened but my source list was empty. Thankfully, following the directions in this thread I was able to do what was necessary. Now, let's see if this works!

Thanks to all.

---

### Post by kristalsoldier on 2007-03-01
> **picpak said:**
> I don't get it, from what I see there are no duplicates in that file. deb and deb-src are two different things.

I've had this problem for weeks; I just live with it.

Well...I am resigned now! I continue to have the same problem.

---

### Post by Kateikyoushi on 2007-03-01
Then your sources list is okay, might be some leftover files in the system.
Try to purge it out. [LINK]("http://ubuntuforums.org/showthread.php?t=140920")

---

### Post by kristalsoldier on 2007-03-01
Hmmm...tried the steps...dd not find anything ofending save for the fact that localpurge does not seem to be installed.

The problem persists! But thanks for looking into my request.

---

### Post by mahy on 2007-03-01
This is your sources.list file. The duplicate lines are colored. Remove the duplicity and you'll be ok. I REALLY don't understand why this is a problem.

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
[COLOR="Green"]deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse[/COLOR]
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe

[COLOR="Red"]deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse[/COLOR]
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe



deb http://archive.canonical.com/ubuntu edgy-commercial main
[COLOR="Red"]deb http://security.ubuntu.com/ubuntu/ edgy-security restricted main universe[/COLOR]
[COLOR="Green"]deb http://archive.ubuntu.com/ubuntu/ edgy-updates restricted main universe[/COLOR]
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe

deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main main-all
deb http://flomertens.keo.in/ubuntu/ edgy main main-all

```

---

### Post by kristalsoldier on 2007-03-01
Well...when I use sudo nano /etc/apt/sources.list I get the following:

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

This is what I can edit...unless there is some other way to edit which throws up the list in which you have made the notations...

---

### Post by kristalsoldier on 2007-03-01
Hi...

Cancel that last post...Stoopid me! OK! Got it fixed now!

Many thanks!

---

### Post by mahy on 2007-03-01
> **kristalsoldier said:**
> Hi...

Cancel that last post...Stoopid me! OK! Got it fixed now!

Many thanks!

Cool, i was really starting to be afraid there's something wrong with you. ;)

---

### Post by kristalsoldier on 2007-03-01
> **mahy said:**
> Cool, i was really starting to be afraid there's something wrong with you. ;)

Oh...that there is!!!!!:-?

---

