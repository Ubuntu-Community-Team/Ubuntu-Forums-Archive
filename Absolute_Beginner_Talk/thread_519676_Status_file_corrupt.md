---
title: "Status file corrupt?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by blithen on 2007-08-07
I just need to know if the status file will remake itself if I delete.
Thanks in advance.

---

### Post by dreadlord_chris on 2007-08-07
uhh... what status file?

---

### Post by blithen on 2007-08-07
Sorry >_>
/var/lib/dpkg/status

---

### Post by blithen on 2007-08-07
Well I'm getting this error when I try to run synaptic and when I try apt-get

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by dreadlord_chris on 2007-08-07
the staus file does not appear to rebuild itself. Could you post the output of:
```

sudo apt-get update

```

---

### Post by blithen on 2007-08-07
```
blithen@sparky:~$ sudo apt-get update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]         
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US              
Get:3 http://wine.budgetdedicated.com feisty Release.gpg [191B]
Ign http://wine.budgetdedicated.com feisty/main Translation-en_US    
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release               
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://wine.budgetdedicated.com feisty Release                  
Hit http://us.archive.ubuntu.com feisty Release                    
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://us.archive.ubuntu.com feisty-updates Release              
Ign http://wine.budgetdedicated.com feisty/main Packages                       
Hit http://security.ubuntu.com feisty-security/restricted Packages   
Hit http://security.ubuntu.com feisty-security/main Sources          
Hit http://security.ubuntu.com feisty-security/restricted Sources    
Hit http://us.archive.ubuntu.com feisty/main Packages                
Hit http://us.archive.ubuntu.com feisty/restricted Packages          
Hit http://us.archive.ubuntu.com feisty/main Sources                 
Hit http://wine.budgetdedicated.com feisty/main Sources              
Hit http://security.ubuntu.com feisty-security/universe Packages     
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://wine.budgetdedicated.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Fetched 4B in 1s (3B/s)  
Reading package lists... Error!
E: Problem parsing dependency Replaces
E: Error occurred while processing compiz-gtk (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

---

### Post by blithen on 2007-08-07
:guitar:

---

### Post by dreadlord_chris on 2007-08-07
sorry, I'm at a loss at this point....

---

