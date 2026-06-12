---
title: "Synaptic is unable to connect to the internet"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Thug14 on 2007-02-25
Synaptic manager fails to update the package list,instead I get an error as follows

"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

"http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required"



while i am able to access the internet using the mozilla browser.I am connected to the LAN of my institute and use a proxy server which I used in the Synaptic manager settings but still no use.Can sum1 help me?

---

### Post by StarscreamD on 2007-02-25
It seems to me that Synaptic is not set up to correctly navigate the proxy: authentication is failing. Recheck Synaptic proxy settings to ensure they are correctly configured.

---

### Post by chewearn on 2007-02-25
How about here:
System -> Preferences -> Network Proxy

---

### Post by Thug14 on 2007-02-25
> **AstalaVista said:**
> How about here:
System -> Preferences -> Network Proxy
I already did that 


> **StarscreamD said:**
> It seems to me that Synaptic is not set up to correctly navigate the proxy: authentication is failing. Recheck Synaptic proxy settings to ensure they are correctly configured.

well i setup the http proxy settings in  Synaptic Manager/Settings/Preferences/network
is there anythin else I need to do?

---

### Post by bapoumba on 2007-02-25
> **Thug14 said:**
> 
well i setup the http proxy settings in  Synaptic Manager/Settings/Preferences/network
is there anythin else I need to do?
Package managers use /etc/apt/apt.conf file to read proxy settings.
[http://www.die.net/doc/linux/man/man5/apt.conf.5.html]("http://www.die.net/doc/linux/man/man5/apt.conf.5.html")
You should look at the "acquire" group. Here is my file, as an example. I do not need authentication:
```

ACQUIRE { 
http::proxy "http://myproxy.mydomain.fr:xxxx"
};
```

---

### Post by Thug14 on 2007-02-25
> **bapoumba said:**
> Package managers use /etc/apt/apt.conf file to read proxy settings.
[http://www.die.net/doc/linux/man/man5/apt.conf.5.html]("http://www.die.net/doc/linux/man/man5/apt.conf.5.html")
You should look at the "acquire" group. Here is my file, as an example. I do not need authentication:
```

ACQUIRE { 
http::proxy "http://myproxy.mydomain.fr:xxxx"
};
```

i tried tht too,it says 

"bash: http::proxy: command not found"

---

### Post by pandu.rs on 2007-02-25
Looks like I have already experienced similar problem.
I removed the following line from /etc/apt/apt.conf

Acquire::http::Proxy "false";

and then it worked fine. hope this helps

---

### Post by bapoumba on 2007-02-25
@ Thug14 : can you post the output to **cat /etc/apt/apt.conf** ?

---

### Post by Thug14 on 2007-02-25
> **bapoumba said:**
> @ Thug14 : can you post the output to **cat /etc/apt/apt.conf** ?

yeah the output I get is 
```
Acquire::http::Proxy "false";
```

---

### Post by Thug14 on 2007-02-25
> **pandu.rs said:**
> Looks like I have already experienced similar problem.
I removed the following line from /etc/apt/apt.conf

Acquire::http::Proxy "false";

and then it worked fine. hope this helps
and this isnt working either :(

---

### Post by bapoumba on 2007-02-25
> **Thug14 said:**
> yeah the output I get is 
```
Acquire::http::Proxy "false";
```
Have you tried what I suggested in post #5 ?
It is actually working for me, and has been working for many people I helped here :)

---

### Post by Thug14 on 2007-02-25
ya i ried tht too but it still isnt working,I guess its some problem with the repositories,cud u give me ur sources.list file??

---

### Post by bapoumba on 2007-02-25
> **Thug14 said:**
> ya i ried tht too but it still isnt working,I guess its some problem with the repositories,cud u give me ur sources.list file??
I'm using edgy. So here is one that should work. But, package managers do not use global proxy settings, you also have to **set up the apt.conf file correctly** and remove any proxy setting in **synaptic** (> Settings > Preferences > Network> Set it to "Direct").
```
## base
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

## fix updates
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

## security
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```

---

### Post by fech on 2007-02-27
Hi everyone, 

I'm really frustrated because I can't update/install anything on my ubuntu EDGY. Everytime i try apt-get update or anything. I'm connecting via proxy with username and password. I get the following errors:

```
Failed to fetch http://snapshots.ekiga.net/ubuntu/dists/edgy/main/i18n/Translation-en_AU.bz2  Could not connect to proxy.swin.edu.au:8080 (136.186.1.14). - connect (111 Connection refused)

```

My /etc/apt/apt.conf file has the following:

ACQUIRE { 
http::proxy "http://username:password@proxy.swin.edu.au:8080"
};

but nothing seems to work. I've also tried modifying the network proxy global configuration but it doesn't work.

Can you guys help me please?

Thanks a lot.

---

### Post by chewearn on 2007-02-27
I saw this [old thread]("http://ubuntuforums.org/showthread.php?t=63496&highlight=apt.conf+http+proxy")

At post #4:
> If you need to authenticate yourself with a proxy that expects an MS Domain, you prepends your userid with the domain and a back-slash, e.g.:
ACQUIRE {
http:proxy "http://domain\user;password@proxy:8080/"
}

Worth a try.

---

### Post by fjpos on 2007-02-28
> **Thug14 said:**
> Synaptic manager fails to update the package list,instead I get an error as follows

"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

"http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required"



while i am able to access the internet using the mozilla browser.I am connected to the LAN of my institute and use a proxy server which I used in the Synaptic manager settings but still no use.Can sum1 help me?
Hello Thug14

I have the same problem. Until I can solve it I copy the Synaptic package name it is trying to update and then go to the command line sudo apt-get install package_name.  Good luck

---

### Post by fech on 2007-02-28
Hey.

I can't get through this problem. I'm getting really desperate. I never had this problem with RPM based distros....

I'm behind a proxy which is proxy.swin.edu.au

I have to use username and password for authentication

if I edit /etc/apt/apt.conf with: 

Acquire::http::Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT"

I get this error with synaptic / apt-get:

**[http://au.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:) Could not connect to proxy.swin.edu.au:8079 (136.186.1.14). - connect (111 Connection refused)**

Please please help me with this matter. I cannot update my edgy....

Thanks.

---

### Post by grottenolm on 2007-02-28
if you has a proxy with authentication required try this proxy setting in in synaptic

 userid:password@ip-proxy like
otto:geheim@192.168.178.34

---

### Post by Thug14 on 2007-03-01
Try this

[http://www.faqs.org/docs/Linux-HOWTO...ver-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO...ver-HOWTO.html)

it worked for me ,even I had the same problem

---

### Post by bapoumba on 2007-03-01
@ Thug14: your link looks broken ;)

---

### Post by jkeyes0 on 2007-03-01
I had the same problem, on a MS domain, and had to use [NTLMAPS]("http://ntlmaps.sourceforge.net/") to handle my proxy authentication. It's not a very effective fix, but it's definitely a good bandage.

---

### Post by y2kprawn on 2007-03-01
same problem here, i have a proxy set up on 172.16.10.2, I can connect from with firefox.
I have removed the proxy settings from the Synaptic package manager.
I have removed the global network proxy setting
I have edited the /etc/apt/apt.conf to look like this

Acquire::http::proxy "Firstname.lastname:password@172.16.10.2:808";

I am getting this error

```
http://ie.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Temporary failure resolving 'password@172.16.10.2'
http://ie.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg: Temporary failure resolving 'password@172.16.10.2'
http://ie.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg: Temporary failure resolving 'password@172.16.10.2'
http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg: Temporary failure resolving 'password@172.16.10.2'
```

Is my format wrong ?

---

### Post by bapoumba on 2007-03-01
> **y2kprawn said:**
> 
Is my format wrong ?
Not that I can see. Is this an ISA proxy ?

---

### Post by y2kprawn on 2007-03-01
Oh, hold on there now, got something. 
Removing all GUI entries for the proxy and changing it to 

```
Acquire::http::proxy "http://R.Allen:password@172.16.10.2:808";
```

To include the http:// part did the job. I think it is an ISA proxy, but its in the student village here, so we are not told what the story is.
Thanks for the speedy reply, hope this works for others as well.
You will have to excuse my ignorane, this is my first serious step into the world of open operating systems. All I need to do now is figure out how to get the radeon card working, dam ATI.
On the upside I put a person onto this proxy site with xbuntu on a 128MB ram celeron 800 laptop. Very sweet !!! So impressed so far. Would like more consistent GUI settings management though.

---

### Post by rfpeake on 2007-03-03
I had the same problem running Edgy (6.10). This worked for me.

Open a terminal (Application -> Accessories -> Terminal).  Enter: sudo apt-get update.
When prompted, enter your password.  You should get a list of packages.  If you don't, check your network proxy setting -- 
System->Preferences->Network Proxy.  Note the setting, probably a manual setting that looks something like
HTTP Proxy: 192.168.0.1, Port:8080.  Select the setting "Direct Network Connection," close the utility.and try
sudo apt-get update again.  Hopefully, you will now get the package list.

Go back to Synaptic and click on Install Updates.  Synaptic should now be able find the server and begin the update process.

Hope this works for you.

---

### Post by chakkaradeep on 2007-04-09
Hi All,

I had the same problem, and found this strange behaviour of Synaptic.

With my proxy authentication settings, apt-get is working and i do have set my **http_proxy** and **ftp_proxy** environment variables in **/etc/environment** too.

Now, if i execute synaptic from menu (which is actually **gksu /usr/bin/synaptic**), synaptic would report that it could not fetch info from repositories and requires proxy authentication. If i execute synaptic from terminal as, **sudo synaptic**, it worked. I changed the menu entry to **sudo /usr/bin/synaptic** and it worked!

Can anybody explain whats happening here ? Is this the proper solution ?

---

### Post by mincho on 2007-05-02
Please post your apt.conf file

---

