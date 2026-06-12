---
title: "Something seems wrong with wget?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-12-19
I just recently did a fresh install of 7.10, but now when I try to install WINE using the guide from WINE HQ, it appears that wget doesn't do anything.

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
(I enter my password, and then it just sits there...)

No terminal messages after that, I don't know what happened...

[EDIT: I just found a file called wget-log in my /home directory, but it's blank.]
And YES I do have a active internet connection >_>

---

### Post by spiderbatdad on 2007-12-19
have you added the key to your keyring manger?  also wine and wine dev are both in synaptic if you have universe and multiverse enabled

---

### Post by RomeReactor on 2007-12-19
Hi. Try it like this:
```
sudo wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | apt-key add -
```

If that doesn't work, run the commands separately:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg
```
```
sudo apt-key add 387EE263.gpg
```

---

### Post by kpkeerthi on 2007-12-19
Try running that in two steps:
```

wget http://wine.budgetdedicated.com/apt/387EE263.gpg

```

Then...
```

sudo apt-key add 387EE263.gpg

```

Once the key is imported, just remove the downloaded file if you want
```

rm 387EE263.gpg

```

---

### Post by anewguy on 2007-12-19
Something else to keep in mind - when Gutsy (7.10) installed for myself and many others, the default repositories where missing.  Go to system/administration/software sources and be sure that at least the first two boxes are checked. then go to synaptic package manager and do a "reload". After that wine will be right in synaptic.:)

---

### Post by chris062689 on 2007-12-19
Actually, it appears the wine server is actually DOWN...
Does anyone have the latest wine version in a .deb perhaps?  Or a mirror?

---

### Post by kpkeerthi on 2007-12-19
> **chris062689 said:**
> Actually, it appears the wine server is actually DOWN...
Does anyone have the latest wine version in a .deb perhaps?  Or a mirror?

No it is not. I can hit that url with firefox now.

---

### Post by chris062689 on 2007-12-19
Hmm, that's odd, whenever I try to access it, it times out.
Anyone think of a fix?

---

### Post by RomeReactor on 2007-12-19
Try pinging the site:
```
ping -c3 wine.budgetdedicated.com
```
also try downloading the gpg key like this:
```
wget 81.171.111.184/apt/387EE263.gpg
```
and then:
```
sudo apt-key add 387EE263.gpg
```

---

### Post by chris062689 on 2007-12-19
chris@ubuntu-laptop:~$ ping -c3 wine.budgetdedicated.com\
> 
PING wine.budgetdedicated.com (81.171.111.184) 56(84) bytes of data.


--- wine.budgetdedicated.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2000ms

chris@ubuntu-laptop:~$ wget 81.171.111.184/apt/387EE263.gpg
--01:42:14--  [http://81.171.111.184/apt/387EE263.gpg](http://81.171.111.184/apt/387EE263.gpg)
           => `387EE263.gpg'
Connecting to 81.171.111.184:80...

---

### Post by RomeReactor on 2007-12-19
That's odd; you're not behind a proxy? as kpkeerthi said, the site works. There must be something interefering with your connection. A DNS issue maybe?

---

### Post by chris062689 on 2007-12-19
I'm not behind a proxy.
What would you recommend me doing?
This never happened before to me.

---

### Post by kpkeerthi on 2007-12-19
> **chris062689 said:**
> chris@ubuntu-laptop:~$ wget 81.171.111.184/apt/387EE263.gpg
--01:42:14-- [http://81.171.111.184/apt/387EE263.gpg](http://81.171.111.184/apt/387EE263.gpg)
=> `387EE263.gpg'
Connecting to 81.171.111.184:80....

Just realized that you missed **http** there in that command. Shouldn't it look like

wget **http://**81.171.111.184/apt/387EE263.gpg

---

### Post by chris062689 on 2007-12-19
Nope that doesn't work.
Why is this happening?  Very, very weird.

---

### Post by kpkeerthi on 2007-12-19
Try with debug mode 
```

wget --debug http://81.171.111.184/apt/387EE263.gpg

```

---

### Post by RomeReactor on 2007-12-19
> **kpkeerthi said:**
> Just realized that you missed **http** there in that command. Shouldn't it look like

wget **http://**81.171.111.184/apt/387EE263.gpg

HTTP is not needed when using ping.

Chris, make sure you don't have any other applications open which might be hogging the bandwidth. Can you ping Google?:
```
ping -c3 www.google.com
```
and can you open other sites in Firefox?

---

### Post by kpkeerthi on 2007-12-19
> 
HTTP is not needed when using ping.

Yeah. I understand that. But I was suggesting the OP to use **http with wget** :)

---

### Post by chris062689 on 2007-12-19
Yeah I can open other sites just fine.
chris@ubuntu-laptop:~$ ping -c3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (74.125.47.103) 56(84) bytes of data.
64 bytes from 74.125.47.103: icmp_seq=1 ttl=244 time=56.5 ms
64 bytes from 74.125.47.103: icmp_seq=2 ttl=244 time=54.1 ms
64 bytes from 74.125.47.103: icmp_seq=3 ttl=244 time=54.7 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10144ms
rtt min/avg/max/mdev = 54.158/55.169/56.572/1.023 ms


Is there anyway for me to install WINE without using the site I cannot access?
(For the meantime.) 

Could you guys think of any problem?

---

### Post by kpkeerthi on 2007-12-19
Did you try with the debug option I posted above?

---

### Post by chris062689 on 2007-12-19
chris@ubuntu-laptop:~$ wget --debug [http://81.171.111.184/apt/387EE263.gpg](http://81.171.111.184/apt/387EE263.gpg)
DEBUG output created by Wget 1.10.2 on linux-gnu.

--02:16:12--  [http://81.171.111.184/apt/387EE263.gpg](http://81.171.111.184/apt/387EE263.gpg)
           => `387EE263.gpg'
Connecting to 81.171.111.184:80... 

--01:54:17--  [http://81.171.111.184/apt/387EE263.gpg](http://81.171.111.184/apt/387EE263.gpg)
           => `387EE263.gpg'
Connecting to 81.171.111.184:80... failed: Connection timed out.
Retrying.

--01:57:27--  [http://81.171.111.184/apt/387EE263.gpg](http://81.171.111.184/apt/387EE263.gpg)
  (try: 2) => `387EE263.gpg'
Connecting to 81.171.111.184:80... failed: Connection timed out.
Retrying.

--02:00:38--  [http://81.171.111.184/apt/387EE263.gpg](http://81.171.111.184/apt/387EE263.gpg)
  (try: 3) => `387EE263.gpg'
Connecting to 81.171.111.184:80... failed: Connection timed out.
Retrying.

--02:03:50--  [http://81.171.111.184/apt/387EE263.gpg](http://81.171.111.184/apt/387EE263.gpg)
  (try: 4) => `387EE263.gpg'
Connecting to 81.171.111.184:80... failed: Connection timed out.
Retrying.

--02:07:03--  [http://81.171.111.184/apt/387EE263.gpg](http://81.171.111.184/apt/387EE263.gpg)
  (try: 5) => `387EE263.gpg'
Connecting to 81.171.111.184:80... failed: Connection timed out.
Retrying.

--02:10:17--  [http://81.171.111.184/apt/387EE263.gpg](http://81.171.111.184/apt/387EE263.gpg)
  (try: 6) => `387EE263.gpg'
Connecting to 81.171.111.184:80... failed: Connection timed out.
Retrying.

--02:13:32--  [http://81.171.111.184/apt/387EE263.gpg](http://81.171.111.184/apt/387EE263.gpg)
  (try: 7) => `387EE263.gpg'
Connecting to 81.171.111.184:80...

---

### Post by RomeReactor on 2007-12-19
> **kpkeerthi said:**
> Yeah. I understand that. But I was suggesting the OP to use **http with wget** :)

Oh, sorry for the confusion :P . Though as far as I know, pinging addresses starting with http doesn't work.

Chris, you could try [going to the site in Firefox]("http://wine.budgetdedicated.com/") to get the .deb package, or see if you can download the package by [pasting the direct link in Firefox]("http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.51~winehq0~ubuntu~7.10-1_i386.deb").

Or, as [spiderbatdad suggested in the first page]("http://ubuntuforums.org/showpost.php?p=3977983&postcount=2"), install Wine from Synaptic, though you would get an older package then. However, I don't know in what way installing a slightly older version would affect you.

---

### Post by chris062689 on 2007-12-19
Both of the WINE related links above fail to load (timed out).
I obtained a .deb from a friend, and that installation worked.

Could this be something my ISP recently started blocking?

---

### Post by RomeReactor on 2007-12-19
Could be, but I highly doubt it...

---

### Post by kpkeerthi on 2007-12-19
Are your running some parental control programs or anything of such type (/etc/hosts file) blocking access to that website?

---

### Post by chris062689 on 2007-12-19
No parental software, this is a fresh install.
This is my /etc/hosts

127.0.0.1	localhost
127.0.1.1	ubuntu-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by RomeReactor on 2007-12-19
You could try disabling IPV6:
```
gksudo gedit /etc/modprobe.d/aliases
```
comment this line out:
```
alias net-pf-10 ipv6
```
and below that one, add:
```
alias net-pf-10 off
```
Save the file, close Gedit, then reboot.

---

### Post by chris062689 on 2007-12-19
Nope, still a timeout.

---

### Post by kpkeerthi on 2007-12-19
If you are paranoid about disabling IPv6 system-wide, try
```

**wget --inet4-only http://81.171.111.184/apt/387EE263.gpg**

```
to use with wget only.

---

### Post by chris062689 on 2007-12-19
Timedout.

Also, I tried accessing it through another computer running XP, and it also timed out.
What the heck is going on here!? x_x

I just reset my router and my modem.
Still cannot connect.
If someone could do me a favor, could you upload wine versions..
[http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.50~winehq0~ubuntu~7.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.50~winehq0~ubuntu~7.10-1_i386.deb)
[http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.49~winehq0~ubuntu~7.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.49~winehq0~ubuntu~7.10-1_i386.deb)
[http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb)
[http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.47~winehq0~ubuntu~7.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.47~winehq0~ubuntu~7.10-1_i386.deb)

I need to see which one works best for me.
Whoever uploads these to somewhere I could access... I would <3 them.

---

