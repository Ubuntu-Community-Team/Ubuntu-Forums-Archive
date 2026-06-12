---
title: "Wine"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Domy on 2008-02-06
Hi, I ve got serious wine problem mate, i drink too much:), just kidding.
I just installed wine. I did that as it said on web page Wine-HQ. But i get this:

d@d-desktop:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
Password:
OK
d@d-desktop:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
--20:02:37--  [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 88.159.206.7, 81.171.111.184
Connecting to wine.budgetdedicated.com|88.159.206.7|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

100%[====================================>] 181           --.--K/s             

20:02:37 (9.50 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [181/181]

d@d-desktop:~$ sudo apt-get update
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US             
Get:2 [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty/main Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:4 [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty Release                      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty-updates Release             
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources                         
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty/main Packages                
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty/restricted Sources
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty/universe Packages
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty/universe Sources
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 4B in 0s (6B/s)  
Reading package lists... Done
d@d-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.14) but 1.0.13-1ubuntu5 is to be installed
        Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
        Depends: libgphoto2-2 (>= 2.4.0) but 2.3.0-0ubuntu4 is to be installed
        Depends: libgphoto2-port0 (>= 2.4.0) but 2.3.0-0ubuntu4 is to be installed
        Depends: libxml2 (>= 2.6.29) but 2.6.27.dfsg-1ubuntu3.1 is to be installed
E: Broken packages


What can i do? Please help me

---

### Post by mikeyphi on 2008-02-06
Install Wine using the Add/Remove application.

---

### Post by Whiffle on 2008-02-06
Looks to me like you're trying to mix gutsy packages with feisty ones in your repos.  Look at the top two lines after you ran the update command.  In case you hadn't noticed, that doesn't work.  They apparently use different libraries.

Do this:

```

gksudo gedit /etc/apt/sources.list.d/winehq.list

```

In there, change everything that says gutsy to feisty, save it, and rerun apt-get update.  It should work after that.

---

### Post by Cariro on 2008-02-06
Post what you typed.
Did you try: ```
sudo apt-get update
```
then
```
sudo apt-get install win
```
?? Never had problems with it, neither have anyone i know.
If this is NOT what you did, then try it.

---

### Post by jaytek13 on 2008-02-06
> **Cariro said:**
> Post what you typed.
Did you try: ```
sudo apt-get update
```
then
```
sudo apt-get install win
```
?? Never had problems with it, neither have anyone i know.
If this is NOT what you did, then try it.


The text may be a bit jobbled up, but he did list that he did all of this in the first post.

---

### Post by Cariro on 2008-02-06
Ok... 
Then i have NOOOO idea.

---

### Post by Domy on 2008-02-17
hi
Whiffle your solution was successful tnx ;)

But now I don't know how to install win applications and run then in wine...
I read the wine documentations and i haven't found/understand it....

Help please! and tnx for previous fast response and help ;)

---

### Post by strongboww on 2008-02-17
how can you open .msi installers with wine?

with right click "open in wine" i tried to install steam and it just did nothing

---

### Post by Domy on 2008-02-17
tnx for help man ;)

---

### Post by Whiffle on 2008-02-17
msiexec  nameoffile.msi


I think.  If you google it theres a couple of steam howtos for wine.

---

### Post by Northsider on 2008-02-17
> **strongboww said:**
> how can you open .msi installers with wine?

with right click "open in wine" i tried to install steam and it just did nothing

You need to run it from the terminal and use the command 'msiexec'.  Make sure you are in the correct folder when you do so.

```
wine msiexec /.wine/c_Drive/steaminstall.msi
```
^^ Something like that.

---

