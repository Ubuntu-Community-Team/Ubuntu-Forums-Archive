---
title: "Problem with aptitude"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by Dbugger on 2008-04-15
When I try to install something, I get this:

Package XXXX is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

it happens with almost all packages! Why?!

---

### Post by Seisen on 2008-04-15
What package are you trying to install and post the output of this command. ```
cat /etc/apt/sources.list
```

---

### Post by Oldsoldier2003 on 2008-04-15
> **Dbugger said:**
> When I try to install something, I get this:

Package XXXX is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

it happens with almost all packages! Why?!
What it means is you are trying to install a package that is not supported in the repos, but is referred to by a  package... Kind of a catch 22 situation. Try this first:
```
sudo apt-get update
sudo apt-get upgrade
```


then if you still have problems you can always look at[ getdeb]("http://www.getdeb.net/") or compile from source if you absolutely must have the application.

---

### Post by Dbugger on 2008-04-15
```
me@host:~$ cat /etc/apt/sources.list

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy main restricted web
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted web
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted web
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

#emesene
deb [http://apt.emesene.org/](http://apt.emesene.org/) ./
deb-src [http://apt.emesene.org/](http://apt.emesene.org/) ./
```

---

### Post by cybil on 2008-04-15
EDIT:  What package are you trying to install?  I assume that your Internet access is working correctly?

---

### Post by Dbugger on 2008-04-15
> **cybil said:**
> It is possible that the Ubuntu install could not verify the repos when you installed, so it commented them out.  Post the output from the command that Seisen stated

Already did! Look 2 posts up.

---

### Post by Dbugger on 2008-04-15
Lots of packages, for example I was using ettercap just fine... then i removed and reinstalled, then suddenly I couldnt re-install it, but tha'ts just an example... happens A LOT.

Look at this...

```
dbugger@mercury:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US         
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]                                                                                            
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US                                                                                          
Get:2 http://es.archive.ubuntu.com gutsy Release.gpg [191B]                                                       
Ign http://es.archive.ubuntu.com gutsy/main Translation-en_US                                                     
Ign http://es.archive.ubuntu.com gutsy/restricted Translation-en_US                                               
Ign http://es.archive.ubuntu.com gutsy/web Translation-en_US                                                      
Ign http://es.archive.ubuntu.com gutsy/universe Translation-en_US                                                 
Ign http://es.archive.ubuntu.com gutsy/multiverse Translation-en_US                                               
Get:3 http://es.archive.ubuntu.com gutsy-updates Release.gpg [191B]                                               
Ign http://es.archive.ubuntu.com gutsy-updates/main Translation-en_US                       
Ign http://es.archive.ubuntu.com gutsy-updates/restricted Translation-en_US                 
Ign http://es.archive.ubuntu.com gutsy-updates/web Translation-en_US                        
Ign http://es.archive.ubuntu.com gutsy-updates/universe Translation-en_US                                         
Ign http://es.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US                                       
Hit http://es.archive.ubuntu.com gutsy Release                                                                    
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US                                                             
Ign http://security.ubuntu.com gutsy-security/web Translation-en_US                                                                    
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US                                                               
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US                                                             
Hit http://es.archive.ubuntu.com gutsy-updates Release                                                            
Hit http://es.archive.ubuntu.com gutsy/main Packages                                                                                                     
Hit http://es.archive.ubuntu.com gutsy/restricted Packages                                                                          
Hit http://security.ubuntu.com gutsy-security Release                                                                               
Hit http://es.archive.ubuntu.com gutsy-updates/main Packages                                                                       
Hit http://es.archive.ubuntu.com gutsy-updates/restricted Packages                                            
Hit http://security.ubuntu.com gutsy-security/main Packages                                                   
Hit http://security.ubuntu.com gutsy-security/restricted Packages                                             
Ign http://apt.emesene.org ./ Release.gpg                                               
Ign http://apt.emesene.org ./ Translation-en_US                                         
Ign http://download.skype.com stable Release.gpg                                        
Ign http://download.skype.com stable/non-free Translation-en_US
Ign http://apt.emesene.org ./ Release          
Ign http://download.skype.com stable Release
Hit http://download.skype.com stable/non-free Packages
Ign http://apt.emesene.org ./ Packages
Ign http://apt.emesene.org ./ Sources
Hit http://apt.emesene.org ./ Packages
Err http://apt.emesene.org ./ Sources
  404 Not Found
Fetched 3B in 21s (0B/s) 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://es.archive.ubuntu.com/ubuntu/dists/gutsy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://es.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://apt.emesene.org/./Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by kellemes on 2008-04-15
For some reason you have "web" in your repositories.. Those don't exist.
backup and edit /etc/apt/sources.list like so..
```
cd /etc/apt
sudo cp sources.list sources.list.backup
gksudo gedit sources.list
```

Replace text with following..
```

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

#deb http://es.archive.ubuntu.com/ubuntu/ gutsy main restricted
#deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://es.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://es.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://es.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://es.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://es.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://es.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

deb http://download.skype.com/linux/repos/debian/ stable non-free

#emesene
#deb http://apt.emesene.org/ ./
#deb-src http://apt.emesene.org/ ./
```

Now post output of ```
sudo apt-get update
```

---

### Post by Dbugger on 2008-04-15
the apt-get update works fine now, but now I get this message...

```
$ sudo apt-get install ettercap
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
  ettercap: Depends: libnet1 (>= 1.1.2-1) but it is not installable
E: Broken packages
```

---

### Post by cybil on 2008-04-15
If that does not fix it, check for partials

```
ls /var/lib/apt/lists/partial/
```

clear anything in there, and run your apt-get update again

---

### Post by Dbugger on 2008-04-15
> **cybil said:**
> If that does not fix it, check for partials

```
ls /var/lib/apt/lists/partial/
```

clear anything in there, and run your apt-get update again

Empty folder... :(

---

### Post by Dbugger on 2008-04-15
> **kellemes said:**
> 
Now post output of ```
sudo apt-get update
```

```
~$ sudo apt-get update
Ign http://download.skype.com stable Release.gpg
Ign http://download.skype.com stable/non-free Translation-en_US     
Get:1 http://es.archive.ubuntu.com gutsy-updates Release.gpg [191B] 
Ign http://es.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://es.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://es.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://es.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Get:2 http://es.archive.ubuntu.com gutsy Release.gpg [191B]         
Ign http://es.archive.ubuntu.com gutsy/universe Translation-en_US              
Ign http://es.archive.ubuntu.com gutsy/multiverse Translation-en_US            
Hit http://es.archive.ubuntu.com gutsy-updates Release               
Hit http://es.archive.ubuntu.com gutsy Release                                 
Ign http://apt.emesene.org ./ Release.gpg                                      
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Ign http://apt.emesene.org ./ Translation-en_US                                
Ign http://download.skype.com stable Release                                   
Hit http://security.ubuntu.com gutsy-security Release                          
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://security.ubuntu.com gutsy-security/restricted Packages    
Hit http://download.skype.com stable/non-free Packages                         
Ign http://apt.emesene.org ./ Release                                          
Hit http://security.ubuntu.com gutsy-security/main Sources           
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources       
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Hit http://security.ubuntu.com gutsy-security/multiverse Sources     
Hit http://es.archive.ubuntu.com gutsy-updates/main Packages         
Hit http://es.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://es.archive.ubuntu.com gutsy-updates/main Sources
Hit http://es.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://es.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://es.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://es.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://es.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://es.archive.ubuntu.com gutsy/universe Packages
Hit http://es.archive.ubuntu.com gutsy/universe Sources
Hit http://es.archive.ubuntu.com gutsy/multiverse Packages
Hit http://es.archive.ubuntu.com gutsy/multiverse Sources
Ign http://apt.emesene.org ./ Packages         
Hit http://apt.emesene.org ./ Packages
Fetched 3B in 1s (2B/s)
Reading package lists... Done
```

---

### Post by Dbugger on 2008-04-15
Please somebody get me a solution for this...

```
:~$ sudo apt-get install ettercap
[sudo] password for dbugger:
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
  ettercap: Depends: libnet1 (>= 1.1.2-1) but it is not installable
E: Broken packages
```

---

### Post by plucky on 2008-04-15
> #deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy main restricted
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy main restricted

I think your problem is you still don't have the main repository enabled in your sources.list.

If you copied the sources.list supplied by **kellemes** then you have to remove the #'s form the two lines shown above.


To do so ```
gksudo gedit /etc/apt/sources.list
``` Remove the #'s from the two lines,save, and then ```
sudo apt-get update
``` and you should be good to go.


Good Luck.

---

