---
title: "Help with shell script for Avira"
date: 2011-12-25
forum: Any Other OS
---

### Post by Andy45 on 2011-12-25
I am trying to set up a weekly scan by Avira antivir. I am trying to use shell script as that is the only thing I think will work. Here is the script:
                       #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; color: rgb(0, 0, 0); widows: 2; font-style: normal; text-indent: 0in; font-variant: normal; font-weight: normal; font-size: 12pt; text-decoration: none; text-align: left; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Times New Roman'; font-size: 12pt; text-align: left; }         #!/bin/bash
# avscan-special
    #
    #
    #Script to run a scheduled Avira Antivirus scan
    #
    clear
    jay@jay-Dell-DM061 ~ $ /etc/crontab
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root
HOME=/
    &#65279;02 21 * * 0 root run-parts  /etc/cron.weekly
    cd ..
    cd ..
    avscan / /home /root /jay /bin /sbin /etc /dev /prov /var /tmp /usr /boot /lib /opt /mnt /media /srv
    exit 0
   
  Could you please tell me if anything is wrong or if there is an easier method to schedule scans?
P.S. this is on linux mint 10 lxde but in the gnome interface.

---

### Post by Perfect Storm on 2011-12-26
Moved to Other OS/Distro Talk.

---

