---
title: "change computer name?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2007-01-14
how do you change your computer name? or is it even possible

---

### Post by Mimsy on 2007-01-14
Yes, it is. I've done it a few times. In the System (menu in the top left corner of Gnome), in Administration -> Networking, it's possible to change the name of your computer in one of the tabs. I don't remember which one, and my Ubuntu system is upstairs, but I have a clear memory of having to reboot to make the changes permanent.

Sorry that was so vague. If you need more detail I can go upstrairs and start up the Ubuntu laptop. Just let me know.

/Mimsy

---

### Post by jordanmthomas on 2007-01-14
Mimsy was right.
Alternatively, you can edit /etc/hosts and change your hostname there
```
jordan@ttysfcker ~ $ cat /etc/hosts
# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1               ttysfcker localhost.localdomain localhost

# IPV6 versions of localhost and co
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
fff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Here is what mine looks like.  My computer is named ttysfcker and to change it, I would need to change it on the 127.0.0.1 line
```
sudo nano /etc/hosts
```
find the line and change it
```
127.0.0.1               [COLOR="Red"]newname[/COLOR] localhost.localdomain localhost
```
Then, restart your networking or reboot

---

### Post by taurus on 2007-01-14
> **jordanmthomas said:**
> Mimsy was right.
Alternatively, you can edit /etc/hosts and change your hostname there
```
jordan@ttysfcker ~ $ cat /etc/hosts
# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1               ttysfcker localhost.localdomain localhost

# IPV6 versions of localhost and co
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
fff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Here is what mine looks like.  My computer is named ttysfcker and to change it, I would need to change it on the 127.0.0.1 line
```
sudo nano /etc/hosts
```
find the line and change it
```
127.0.0.1               [COLOR="Red"]newname[/COLOR] localhost.localdomain localhost
```
Then, restart your networking or reboot

If you decide to change the name in /etc/hosts, you better change it in /etc/hostname with the same name or you can't use sudo and some other networks apps as well!

---

### Post by jordanmthomas on 2007-01-14
woops, thanks for catching that one.

---

### Post by obsidion on 2007-01-14
> **jordanmthomas said:**
> woops, thanks for catching that one.

  You see a lot of posts here and on the newsgroups from people who have made just this mistake and had sudo removed from them.

I do it this way, works for me :)

127.0.0.1       localhost.localdomain  localhost
127.0.1.1       tscii
10.1.1.7        tscii.corn

 I have the localhost.localdomain localhost

because I find that a lot of server based games work better and faster locally if you have that line.
The 10.1.1.7 which is my address on the router allows me to use that address in sendmail or similar without it having a tantrum

---

### Post by kaviyesh on 2007-01-16
Hi,

I changed the hostname by editing /etc/hostname.... But now sudo doesn't work :(  and I get the message "unable to lookup 'new hostname' via gethostname().  What can be done to rectify the mistake?

Thanks
Kaviyesh

Problem solved: I logged in recovery mode and made changes in /etc/hosts

---

