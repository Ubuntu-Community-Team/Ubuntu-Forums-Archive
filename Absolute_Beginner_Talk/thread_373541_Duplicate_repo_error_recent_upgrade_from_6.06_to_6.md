---
title: "Duplicate repo error recent upgrade from 6.06 to 6.10"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by OrangeCrate on 2007-03-01
**I recently upgraded from Dapper to Edgy. I just ran the update manager and it showed that my system was up to date. I hit the check button, got the following error, and two updates:**

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)

**Using this command -  gksudo gedit /etc/apt/sources.list - here's my source list:**

(gedit:9546): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

**Is this error something to be concerned about? And if so, would someone be able to help me understand why I got that error, and what I might be able to do to fix it?**

---

### Post by OrangeCrate on 2007-03-01
Bump

---

### Post by Kateikyoushi on 2007-03-01
Are you sure that's your entire sources.list because I can't find the duplicated entries.

The following should diplay the file.

```
cat /etc/apt/sources.list
```

---

### Post by nudnik on 2007-03-01
> **OrangeCrate said:**
> **I recently upgraded from Dapper to Edgy. I just ran the update manager and it showed that my system was up to date. I hit the check button, got the following error, and two updates:**

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)

**Using this command -  gksudo gedit /etc/apt/sources.list - here's my source list:**

(gedit:9546): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

**Is this error something to be concerned about? And if so, would someone be able to help me understand why I got that error, and what I might be able to do to fix it?**

 Try opening Synaptic. Click on Settingings, then Repositories. Scroll along the window and see if there are duplicates. If so, click remove on the identical entries. This might actually solve the trouble, if not, see mascot below. You are not alone. May the force be with you!

---

### Post by nudnik on 2007-03-01
I gave you the instructions for Gnome above. I realised you are using KDE (I'm slow). Hopefully something similar can be done within the KDE environment as I am only properly familiar with Gnome. :shock:

---

### Post by OrangeCrate on 2007-03-02
> **Kateikyoushi said:**
> Are you sure that's your entire sources.list because I can't find the duplicated entries.

The following should diplay the file.

```
cat /etc/apt/sources.list
```

Yes, that's it, and why I'm confused about getting the error...

cat /etc/apt/sources.list

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

---

### Post by Kateikyoushi on 2007-03-02
I would add universe multiverse to the first lines, currently have no better idea, make a backup first just in case. Then try it again.

---

### Post by OrangeCrate on 2007-03-02
> **nudnik said:**
> Try opening Synaptic. Click on Settingings, then Repositories. Scroll along the window and see if there are duplicates. If so, click remove on the identical entries. This might actually solve the trouble, if not, see mascot below. You are not alone. May the force be with you!

In 6.10, I don't find the long list of repositories as there was in Dapper. The first four options are checked by default. I have not changed any settings here.

Community maintained open source software (universe)

Canonical supported open source software (main)

Software restricted by copyright or legal issues (multiuniverse)

Proprietary drivers for devices (restricted)

---

### Post by OrangeCrate on 2007-03-02
> **nudnik said:**
> I gave you the instructions for Gnome above. I realised you are using KDE (I'm slow). Hopefully something similar can be done within the KDE environment as I am only properly familiar with Gnome. :shock:

No, I'm using Gnome. See my other post for my response to your instructions.

---

### Post by OrangeCrate on 2007-03-02
> **Kateikyoushi said:**
> I would add universe multiuniverse to the first lines...

I'm sorry, I'm not sure how to do that.

---

Something I just remembered. I had accidentally deleted a repository in Dapper as I was following a tutorial on adding repositories, and based on the instructions from another forum member, I replaced the original Dapper source list, with an auto-generated one. After that, everything seemed to be working fine.

I wonder if when I updated from Dapper to Edgy, if that would have created a duplicate situation, but as you pointed out, if there are duplicates, the source list should tell me, and it doesn't.

---

### Post by OrangeCrate on 2007-03-02
> **OrangeCrate said:**
> 
Something I just remembered. I had accidentally deleted a repository in Dapper as I was following a tutorial on adding repositories, and based on the instructions from another forum member, I replaced the original Dapper source list, with an auto-generated one. After that, everything seemed to be working fine.

I wonder if when I updated from Dapper to Edgy, if that would have created a duplicate situation, but as you pointed out, if there are duplicates, the source list should tell me, and it doesn't.

Here's a link to the thread where I had a problem with the Dapper repositories:

[http://ubuntuforums.org/showthread.php?t=362838](http://ubuntuforums.org/showthread.php?t=362838)

I would have thought that upgrading to Edgy would have simply replaced the Dapper information with new Edgy information, but maybe there is a conflict? (I'm just guessing here.)

---

### Post by Kateikyoushi on 2007-03-02
I upgraded that way too and works for me, my only idea is that it did not like the server was in it several times.

---

### Post by OrangeCrate on 2007-03-02
> **Kateikyoushi said:**
> I upgraded that way too and works for me, my only idea is that it did not like the server was in it several times.

I just opened the update manager, to look at the settings again, and when I closed it, it told me that the repositories had changed, and use the check button. When I did, I got this error:

Could not download all repository indexes

[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.bz2:) Could not open file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages - open (2 No such file or directory)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.bz2:) Could not open file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages - open (2 No such file or directory)

And then, I get the duplicate entry notice from my original post again.

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)

Edit:

I had seen that "could not download all repository indexes" originally, but had failed to make note of it. The above is now the complete error I have been getting, and the reason for starting this thread.

---

### Post by Kateikyoushi on 2007-03-02
Okay seems it is not the list, then let's try to clean out the system, see link for instructions. [LINK]("http://ubuntuforums.org/showthread.php?t=140920")

---

### Post by OrangeCrate on 2007-03-02
> **Kateikyoushi said:**
> Okay seems it is not the list, then let's try to clean out the system, see link for instructions. [LINK]("http://ubuntuforums.org/showthread.php?t=140920")

Thank you. This is going to take me a little to time to do. I'll report back when I've finished. Please stay with me here in this thread, your help is highly appreciated.

---

### Post by OrangeCrate on 2007-03-02
> **Kateikyoushi said:**
> Okay seems it is not the list, then let's try to clean out the system, see link for instructions. [LINK]("http://ubuntuforums.org/showthread.php?t=140920")

O.K., all done. Sorry it took me some time, I was reading and learning as I went along here, and was trying to be careful...

---

### Post by Kateikyoushi on 2007-03-02
Do you still get the erros if you try to update ?

---

### Post by OrangeCrate on 2007-03-02
> **Kateikyoushi said:**
> Do you still get the erros if you try to update ?

Yes, same errors.

---

### Post by Kateikyoushi on 2007-03-02
I searched and you might have a corrupted database.
Try the following
```
sudo apt-get clean
sudo apt-get check
```

---

### Post by OrangeCrate on 2007-03-02
I just received one update:

Ubuntu - docs
Ubuntu documentation project
6.10.4 to 6.10.4.2

I've gone ahead an installed that update.

Edit: We were posting at the same time, I'll follow your instructions now.

---

### Post by OrangeCrate on 2007-03-02
> **Kateikyoushi said:**
> I searched and you might have a corrupted database.
Try the following
```
sudo apt-get clean
sudo apt-get check
```

Done.

---

### Post by Kateikyoushi on 2007-03-02
Try to sudo aptitude update.

---

### Post by OrangeCrate on 2007-03-02
> **Kateikyoushi said:**
> Try to sudo aptitude update.

Done. Here's the read-out:

sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Fetched 3B in 4s (1B/s)
Reading package lists... Done

---

### Post by Kateikyoushi on 2007-03-02
So far seems okay, and the output of the following ?

sudo aptitude update

---

### Post by OrangeCrate on 2007-03-02
sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Fetched 3B in 5s (1B/s)  
Reading package lists... Done

---

### Post by Kateikyoushi on 2007-03-02
Sorry, that was already.

sudo aptitude upgrade

---

### Post by OrangeCrate on 2007-03-02
sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by Kateikyoushi on 2007-03-02
Then it is working properly and your system is up to date.

---

### Post by OrangeCrate on 2007-03-02
> **Kateikyoushi said:**
> Then it is working properly and your system is up to date.

Thank you for your help. By the way, we have family in both the Yokohama and Matsumoto City areas. Beautiful country, I'm envious that you live in Tokyo.

---

### Post by Kateikyoushi on 2007-03-02
I am glad it worked out, I also moved out to the outskirts of Tokyo as I prefer the garden towns, a friend of mine has a house in Yokohama now that's lucky beutiful place, just been there for chinese new year.

---

### Post by OrangeCrate on 2007-03-02
When my wife and I lived in Yokohama years ago, we lived in Motomachi (near Chinatown). Chinatown is where we head for immediately on arrival - just to eat. Incredible food - great restaurants. Chinese New Year there must be a real hoot! I'd love to be there for it sometime, but that's a bad time of the year for us to get away. Maybe someday... Thanks again for all your help, it's highly appreciated.

---

