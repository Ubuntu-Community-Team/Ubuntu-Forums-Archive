---
title: "Something is wrong with wget"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-03
Whatever I download with wget using terminal gives this error: ```
Resolving somewebsite.com... failed: Temporary failure in name resolution.

```
I tried the links in firefox and they are downloading as usuall. but whenever I want to download anything using wget it gives that kinda error!

What's wrong? what can I do?
Please Help!

---

### Post by steve.horsley on 2006-05-03
Try **ping somewebsite.com** and see what it says. It shoudl come back and say what IP address it's pinging. If if does (whether or not the ping succeeds) then DNS name resolution is working. If not, then the error message may help.
> steve@StevesPC:~$ ping ubuntuforums.org
PING ubuntuforums.org (82.211.81.186) 56(84) bytes of data.

Alternatively, try **wget --noproxy** just in case a proxy is defined in your environment somewhere

---

### Post by halfvolle melk on 2006-05-03
Wierd ...
Could you post the exact wget command you're trying, along with the out put of this:
```
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by Isoss on 2006-05-03
Everything concerning the network interface and DNS is right ... I am sure.
I'll post here two wget download attempts for Automatix and mercury-messenger:

Automatix:
```
isos@localhost:~$  wget http://beerorkid.com/automatix/automatix_5.8-1_i386.deb --23:44:10--  http://beerorkid.com/automatix/automatix_5.8-1_i386.deb
           => `automatix_5.8-1_i386.deb'
Resolving beerorkid.com... failed: Temporary failure in name resolution.

```

Mercury-Messenger:
```
isos@localhost:~$ sudo wget http://easynews.dl.sourceforge.net/sourceforge/projeto-messias/mercury-messenger_1710_S7_i386.deb
--23:42:12--  http://easynews.dl.sourceforge.net/sourceforge/projeto-messias/mercury-messenger_1710_S7_i386.deb
           => `mercury-messenger_1710_S7_i386.deb'
Resolving easynews.dl.sourceforge.net... failed: Temporary failure in name resolution.

```

Trying the no-proxy:
```
isos@localhost:~$  wget --no-proxy http://beerorkid.com/automatix/automatix_5.8-1_i386.deb
--23:47:36--  http://beerorkid.com/automatix/automatix_5.8-1_i386.deb
           => `automatix_5.8-1_i386.deb'
Resolving beerorkid.com... failed: Temporary failure in name resolution.
isos@localhost:~$ isos@localhost:~$  wget --no-proxy http://beerorkid.com/automatix/automatix_5.8-1_i386.deb
bash: isos@localhost:~$: command not found
isos@localhost:~$ --23:47:36--  http://beerorkid.com/automatix/automatix_5.8-1_i386.deb
bash: --23:47:36--: command not found
isos@localhost:~$            => `automatix_5.8-1_i386.deb'
> Resolving beerorkid.com... failed: Temporary failure in name resolution.
>

```
and it just stops at the last line " > " as if the process is still going ...

---

### Post by Isoss on 2006-05-03
Everything concerning the network interface and DNS is right ... I am sure.
I'll post here two wget download attempts for Automatix and mercury-messenger:

Automatix:
```
isos@localhost:~$  wget http://beerorkid.com/automatix/automatix_5.8-1_i386.deb --23:44:10--  http://beerorkid.com/automatix/automatix_5.8-1_i386.deb
           => `automatix_5.8-1_i386.deb'
Resolving beerorkid.com... failed: Temporary failure in name resolution.

```

Mercury-Messenger:
```
isos@localhost:~$ sudo wget http://easynews.dl.sourceforge.net/sourceforge/projeto-messias/mercury-messenger_1710_S7_i386.deb
--23:42:12--  http://easynews.dl.sourceforge.net/sourceforge/projeto-messias/mercury-messenger_1710_S7_i386.deb
           => `mercury-messenger_1710_S7_i386.deb'
Resolving easynews.dl.sourceforge.net... failed: Temporary failure in name resolution.

```

Trying the no-proxy:
```
isos@localhost:~$  wget --no-proxy http://beerorkid.com/automatix/automatix_5.8-1_i386.deb
--23:47:36--  http://beerorkid.com/automatix/automatix_5.8-1_i386.deb
           => `automatix_5.8-1_i386.deb'
Resolving beerorkid.com... failed: Temporary failure in name resolution.
isos@localhost:~$ isos@localhost:~$  wget --no-proxy http://beerorkid.com/automatix/automatix_5.8-1_i386.deb
bash: isos@localhost:~$: command not found
isos@localhost:~$ --23:47:36--  http://beerorkid.com/automatix/automatix_5.8-1_i386.deb
bash: --23:47:36--: command not found
isos@localhost:~$            => `automatix_5.8-1_i386.deb'
> Resolving beerorkid.com... failed: Temporary failure in name resolution.
>

```
and it just stops at the last line " > " as if the process is still going ...

---

### Post by Isoss on 2006-05-03
Sorry for the repitition .. it's the browser's mistake ;)

---

### Post by Isoss on 2006-05-03
Sometimes I wish there is a NUDGE in forums to atract attentions ... SOMEBODY HELP! ... I can't wait till tomorrow cuz by then the thread would had been gone to the 4th page ... So please somebody give me a solution! ... this is bad ... your help will be so much appriciated.

---

### Post by steve.horsley on 2006-05-04
You didn't post the ping output, but since you are sure it's working, I guess the next step is to use ping to find the IP address and then substitute the IP address for the name in the URL that you feed to wget.

Perhaps try wget -4 whatever-url to forcr use of ipv4 only.

---

### Post by Isoss on 2006-05-04
sorry .. the ping is working, but I didn't get it! can u please make the command more clear?

here is the pinging of beerorkid.com:
```
isos@ubuntu:~$ sudo ping beerorkid.com
PING beerorkid.com (208.97.133.175) 56(84) bytes of data.

```

---

