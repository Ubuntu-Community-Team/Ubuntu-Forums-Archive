---
title: "error &quot;sudo apt-get update&quot;"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by djeepgu on 2007-05-19
> sudo apt-get update
Err [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) feisty Release.gpg
  Could not connect to ro.archive.ubuntu.com:80 (192.129.4.120). - connect (113 No route to host)
Err [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) feisty/main Translation-en_US               
  Could not connect to ro.archive.ubuntu.com:80 (192.129.4.120). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                   
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (113 No route to host)
Err [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) feisty/restricted Translation-en_US         
  Could not connect to ro.archive.ubuntu.com:80 (192.129.4.120). - connect (113 No route to host)
Err [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) feisty/universe Translation-en_US           
  Could not connect to ro.archive.ubuntu.com:80 (192.129.4.120). - connect (113 No route to host)
Err [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) feisty/multiverse Translation-en_US         
  Could not connect to ro.archive.ubuntu.com:80 (192.129.4.120). - connect (113 No route to host)
Err [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) feisty-updates Release.gpg                  
  Could not connect to ro.archive.ubuntu.com:80 (192.129.4.120). - connect (113 No route to host)
0% [Connecting to ro.archive.ubuntu.com (192.129.4.120)] [Connecting to secur 

:mad: help please

---

### Post by ugm6hr on 2007-05-19
You need to be connected to the internet - otherwise the Installer won't be able to find any of the requested packages.

---

### Post by djeepgu on 2007-05-19
> **ugm6hr said:**
> You need to be connected to the internet - otherwise the Installer won't be able to find any of the requested packages.

i am connected, i'm posting from the computer with the problems :KS
I am behind a proxy if this could be the problem...

---

### Post by bapoumba on 2007-05-20
How did you set up your proxy ?
What is the output to:
```
cat /etc/apt/apt.conf
```

---

### Post by hclima on 2007-07-04
Hi.
I'm having exactly the same problem.
I've already looked at a lot of post in this forum but none of them has work.
So, I'm behind a proxy with authentication.
I dont't have any file /etc/apt/apt.conf but I've a directory named /etc/apt/apt.conf.d where I've a file named proxy with the follow content:
```

Acquire::http
{
  Proxy "<proxy-url>:3128";
  ProxyLogin
  {
     "USER <username>";
     "PASS <password>";
  }
}

Acquire::ftp
{
  Proxy "<proxy-url>:3128";
  ProxyLogin
  {
     "USER <username>";
     "PASS <password>";
  }
}

```

in the file /etc/bash.bashrc I've someting like:

```

...
# Configure the proxy information
export HTTP_PROXY=<username>:<password>@<proxy-url>:3132
export HTTPS_PROXY=<username>:<password>@<proxy-url>:3132
export FTP_PROXY=<username>:<password>@<proxy-url>:3132
...

```

My sources list file (/etc/apt/sources.list) is like
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ao.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://ao.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security multiverse

#edgy-updates main restricted universe 
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe
#edgy-updates main restricted universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe

```

Some lines from apt-get update command:

```

Err http://us.archive.ubuntu.com edgy-updates Release.gpg                                                                                                    
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31). - connect (113 No route to host) [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com feisty Release.gpg                                                                                                             
  Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (113 No route to host) [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com feisty/main Translation-en_US                                                                                                 
  Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (113 No route to host) [IP: 91.189.89.6 80]
Err http://ao.archive.ubuntu.com feisty-backports Release.gpg                                                                                               
  Could not connect to ao.archive.ubuntu.com:80 (91.189.89.6). - connect (113 No route to host) [IP: 91.189.89.6 80]

```

I can't even download anything with wget, but with firefox, I can go [almost] everywhere.

Any ideas?

Thanks in advance...

---

### Post by moore.bryan on 2007-07-04
[quote=hclima;2961692]Hi.
```

Acquire::http
{
  Proxy "<proxy-url>:3128";
  ProxyLogin
  {
     "USER <username>";
     "PASS <password>";
  }
}

Acquire::ftp
{
  Proxy "<proxy-url>:3128";
  ProxyLogin
  {
     "USER <username>";
     "PASS <password>";
  }
}

```in the file /etc/bash.bashrc I've someting like:
```

...
# Configure the proxy information
export HTTP_PROXY=<username>:<password>@<proxy-url>:3132
export HTTPS_PROXY=<username>:<password>@<proxy-url>:3132
export FTP_PROXY=<username>:<password>@<proxy-url>:3132
...

```
*i'm not too sure, but one of these looks like it's opening port 3128 and the other 3132.  perhaps that's your issue?*

---

### Post by moore.bryan on 2007-07-04
> **hclima said:**
> Hi.
```

Acquire::http
{
  Proxy "<proxy-url>:3128";
  ProxyLogin
  {
     "USER <username>";
     "PASS <password>";
  }
}

Acquire::ftp
{
  Proxy "<proxy-url>:3128";
  ProxyLogin
  {
     "USER <username>";
     "PASS <password>";
  }
}

```in the file /etc/bash.bashrc I've someting like:
```

...
# Configure the proxy information
export HTTP_PROXY=<username>:<password>@<proxy-url>:3132
export HTTPS_PROXY=<username>:<password>@<proxy-url>:3132
export FTP_PROXY=<username>:<password>@<proxy-url>:3132
...

```
*i'm not too sure, but one of these looks like it's opening port 3128 and the other 3132.  perhaps that's your issue?*

---

### Post by mooha on 2007-07-04
```
Acquire::http::Proxy "http://myusername:mypassword@myserver.com:8080/";
```

I wrote that on my /etc/apt/apt.conf file that's it just one line. and it works very well for all protocols.
note: I don't remember if it worked for me right after I added it or after I rebooted, try them both. but rebooting I don't think you need to.


Good luck

---

### Post by bapoumba on 2007-07-05
> **mooha said:**
> ```
Acquire::http::Proxy "http://myusername:mypassword@myserver.com:8080/";
```

I wrote that on my /etc/apt/apt.conf file that's it just one line. and it works very well for all protocols.
note: I don't remember if it worked for me right after I added it or after I rebooted, try them both. but rebooting I don't think you need to.


Good luck
This is also the way I do it (but the proxy does not require authentication). Make sure it is set to "direct" in synaptic, and to remove other proxy definitions in the other conf files.

---

### Post by hclima on 2007-07-06
Hi.
Thank you everyone.

The post from mooha has worked well.

Cheers.

---

