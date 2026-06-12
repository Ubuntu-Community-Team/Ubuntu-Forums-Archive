---
title: "Can't install Kubuntu desktop in Feisty 7.04"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by rallenk on 2007-06-05
I have tried using synaptic and Terminal commands to install
Kubuntu on Feisty but to no avail. I get an error message I think
about repositories..not sure....will have to re-read it this evening.
Any ideas? Is there a bug?

---

### Post by Lord Illidan on 2007-06-05
Without the right error message, we can't really help. However, the problem might be that internet access isn't working well, or your repositories are down.

---

### Post by taurus on 2007-06-05
Post the outputs of those two commands from a terminal.

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by rallenk on 2007-06-06
Ok....I was able to get the entire Kubuntu desktop and dependencies to download and install....However,
now I am not given the choice on login to select which to use...KDE or GDE....
any help would be appreciated

---

### Post by Lord Illidan on 2007-06-06
> **rallenk said:**
> Ok....I was able to get the entire Kubuntu desktop and dependencies to download and install....However,
now I am not given the choice on login to select which to use...KDE or GDE....
any help would be appreciated

KDE or GNOME, in that case. At loginscreen look around for an options button, select sessions, and then chose KDE or GNOME.

---

### Post by rallenk on 2007-06-06
Thanks Much......:popcorn:

---

### Post by sailor2001 on 2007-06-06
ctrl/alt/backspace to get to splash screen to check options

---

### Post by rallenk on 2007-06-07
hmmm...I have no option for KDE   only GNOME and xclient.....
Als, I re-installed KDE desktop and when I get to the Postfix screen, I have no way out from the following screen...

&#9474;  
 &#9474; You have several choices for general configuration at this point.  If     &#8593;  
 &#9474; you have your debconf priority set to 'low' or 'medium', you will be      &#9646;  
 &#9474; asked more questions later.  You can always run "dpkg-reconfigure         &#9618;  
 &#9474; --priority=low postfix" at a later point if you want to see these         &#9618;  
 &#9474; questions again.                                                          &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; No configuration - IF YOU WANT THE INSTALL TO LEAVE YOUR CONFIG ALONE,    &#9618;  
 &#9474; CHOOSE THIS OPTION.  No configuration changes will be done now:  If you   &#9618;  
 &#9474; have not already configured Postfix, your mail system will be broken and  &#9618;  
 &#9474; should not be used. You must then do the configuration yourself by        &#9618;  
 &#9474; editing /usr/share/postfix/main.cf.dist and saving your changes as        &#9618;  
 &#9474; /etc/postfix/main.cf, or by running dpkg-reconfigure Postfix.  main.cf    &#9618;  
 &#9474; will not be modified by the Postfix install process.                      &#9618;  
 &#9474;                                                                           &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
                                                                         
Hitting enter or clicking anything brings no response....consequently I simply close the terminal window....but still no option for KDE

---

### Post by taurus on 2007-06-07
You need to hit the Tab key to highlight the <OK>.  Then, hit the Return to accept it.

---

