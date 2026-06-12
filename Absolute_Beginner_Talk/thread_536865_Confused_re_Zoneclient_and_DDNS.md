---
title: "Confused re Zoneclient and DDNS"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by tbone02 on 2007-08-28
I'm a noobie who has a ubuntu 6.06 LAMP server installed.  I've got SSH working and can log onto the server from within my LAN.  I've also logged onto the server from outside the LAN.  I have a domain name, and have included it as a zone on zoneedit, and I have forwarded ports 22 and 80 for SSH and Apache.  Right now I have the domain pointed to the last WAN IP address I had.  Of course, the ISP has changed the dynamic IP address and now my domain is no longer pointed at my router/server.

I know I need to run a client to reset the WAN IP address when it changes.

I used zoneedit as my DNS because it had support for doing this.  I've been trying to figure out how to use zoneclient, but being a noobie I don't understand the (admittedly basic) instructions on the website.

Does anyone know of a "howto" for zoneclient for a noobie to Linux?  Specifically, I need to know how to "install" the python code into the proper file and how to run the code periodically, e.g. hourly.  I have found some code for including in the etc/cron-hourly/ directory, but I have tried and could not figure out how to include the code in that directory so that it will run.

Any help is greatly appreciated!

---

### Post by dstew on 2007-08-28
I don't know how much you know already, but a good introduction to configuring **cron** tasks is [here.]("https://help.ubuntu.com/community/CronHowto")

Also, post your **/etc/crontab** listing to the forum, if you have configured it but find it isn't working.

---

### Post by tbone02 on 2007-08-28
thanks for your response, dstew.

I have read the cron page and will use that eventually.

However, I decided to run zoneclient.py with the options I will be using form the terminal to troubleshoot it before incorporating it into a cron.

It runs but it never gets past accessing Linksys Status page (I have a Linksys router).

Here is my command line:

sudo python /usr/local/bin/zoneclient.py -d /home/zoneclient/ -L admin -l -v MyUserName MyPassword mydomain.com,*.mydomain.com

And here is the .log file:

zoneclient/0.57s
zoneclient.py: Tue Aug 28 19:36:36 2007
zoneclient.py: logging to /home/zoneclient/zoneclient.log
zoneclient.py: opt_directory set to /home/zoneclient/
zoneclient.py: opt_Linksys_password = MyLinksysPW
zoneclient.py: opt_username = MyUserName
zoneclient.py: opt_password = MyPassword
zoneclient.py: opt_hostnames = mydomain.com,*mydomain.com
zoneclient.py: PWD = /home/zoneclient
zoneclient.py: Datfile = /home/zoneclient/zoneclient.dat
zoneclient.py: Errfile = /home/zoneclient/zoneclient.err
zoneclient.py: Waitfile = /home/zoneclient/zoneclient.wait
zoneclient.py: Htmlfile = /home/zoneclient/zoneclient.html
zoneclient.py: Tempfile = /home/zoneclient/zoneclient.tmp
zoneclient.py: Searching default route on sys.platform = linux2
zoneclient.py: Linux default route detection for router.
zoneclient.py: Trying linksys router at 192.168.1.1
zoneclient.py: Attempting to access Linksys status page: /Status.htm (BEFSR41)
zoneclient.py: Attempting to access Linksys status page: /RouterStatus.htm (RT3
zoneclient.py: Attempting to access Linksys status page: /Status_Router.asp (WR$
zoneclient.py: Attempting to access Linksys status page: /Status_Router.asp (WR$
zoneclient.py: Attempting to access Linksys status page: /Status_Router.asp (WR$
zoneclient.py: Attempting to access Linksys status page: /Status_Router.htm (un$


Add that's it.  As far as I can tell it never succesfully retrieved the WAN IP from the router or uploaded it to the zoneedit site.

Can anyone help???

---

### Post by tbone02 on 2007-08-30
I successfully ran zoneclient.py using the -r option and the appropriate zoneedit website ([http://dynamic.zoneedit.com/checkip.html](http://dynamic.zoneedit.com/checkip.html)).

I still cannot get the -L option to work with my linksys router.  I have a WRT-54G (I think).

I decided just to use the -r option until I could get the -L option to work.  I created a cronjob using the -r option so that my IP would be updated every hour.  I first made zoneclient.conf including the following:

```
-d /home/zoneclient/ -r http://dynamic.zoneedit.com/checkip.html -v -l Username Password domain.com,*.domain.com
```

Then I typed:

```
crontab -e
```

In the crontab file I included:

```
# m h  dom mon dow   command
33 * * * * sudo python /usr/local/bin/zoneclient.py --optfile /home/zoneclient/zoneclient.conf
```

I attempted several variations of this crontab code such as removing the "sudo," removing the "sudo python," removing the --optfile command and entering all the options in the crontab.  In order to check to make sure my zoneclient.conf file had no errors, I ran zonclient from the terminal line using --optfile and the zoneclient.conf and it worked fine.  I am basically at a loss for what to try now.

My understanding of the crontab is that my code above should run every hour on the 33rd minute of the hour.  However, when I checked the zoneclient.log file it had the log from the last time I ran zoneclient at the terminal.

Anybody?

---

### Post by dstew on 2007-08-30
The crontab file you listed is for you as a user, correct?

If you are using a user crontab file, the command must be executable by that user. If you need to use sudo to run your command, you probably need to put it into the root crontab file, in the /etc directory. Permissions are also modified by the /etc/cron.allow and /etc/cron.deny files.

A great short explanation of running automated tasks in Linux is [here]("http://www.linux.org/lessons/interm/c622.html").

---

### Post by htpeng on 2007-11-02
I have the exact same router and got it to work by change zoneclient.py - line 573.  Set my router's IP
  Linksys_host = "192.168.1.1"

In my opinion, if you can access your router web page, the zoneclient.py should work for any router.  All you need to do is to hard-code the page such Status_Router.htm, then hard-code the router IP address (as above).  Then all zoneclient.py does is sending HTTP request for Status_Router.htm, then fetching the external IP from it.

---

