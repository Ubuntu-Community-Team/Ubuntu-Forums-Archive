---
title: "terminal help"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by flash2lightning on 2006-12-02
when i open the terminal, it has

jack@Jack's Ubuntu:~$

and when i try to do anything starting with sudo it gives me this

sudo: unable to look up Jack's Ubuntu via gethostname()

help!

---

### Post by taurus on 2006-12-02
Did you happen to change/modify your /etc/hosts and/or /etc/hostname?  Make sure the name in /etc/hostname is the same name that you have in /etc/hosts...

```
cat /etc/hostname /etc/hosts
```

---

### Post by flash2lightning on 2006-12-02
there is no /etc/hostname or /etc/hosts

---

### Post by taurus on 2006-12-02
Are you sure you don't have those two files???  What's the output of this command, from a terminal?

```
ls -la /etc/host*
```

---

### Post by flash2lightning on 2006-12-02
wait.. they're there but my hostname is Jack's Ubuntu and my hosts is jack-desktop

---

### Post by taurus on 2006-12-02
Can you paste that output here?

```
cat /etc/hostname /etc/hosts
```

---

### Post by flash2lightning on 2006-12-02
Jack's Ubuntu
127.0.0.1 localhost Jack's Ubuntu
127.0.1.1 jack-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by taurus on 2006-12-02
So, do you want to call your desktop "Jack's Ubuntu" or "jack-desktop"?  I assume you want to call it "jack-desktop" then.  You need to replace the Jack's Ubuntu with jack-desktop in /etc/hostname and remove the Jack's Ubuntu from your /etc/hosts...

/etc/hostname
```
jack-desktop
```
/etc/hosts
```

127.0.0.1 localhost
127.0.1.1 jack-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by flash2lightning on 2006-12-02
it says permission denied...

---

### Post by taurus on 2006-12-02
Boot into recovery mode from GRUB menu and edit them...

```
nano -w /etc/hosts  /etc/hostname
```

---

### Post by flash2lightning on 2006-12-02
it says permission denied

---

### Post by taurus on 2006-12-02
> **flash2lightning said:**
> it says permission denied
Permission denied on what?  :confused:

---

### Post by flash2lightning on 2006-12-02
when i make both lines jack-desktop and press ctl-x to exit, then y to save changes, it says "File Name to Write: /etc/hosts" when i press enter, it says permission denied

---

### Post by flash2lightning on 2006-12-02
[ Error writing /etc/hosts: Permission denied ], specifically

---

### Post by taurus on 2006-12-02
Did you boot into recovery mode first???

---

### Post by flash2lightning on 2006-12-02
whups
ok here goes

---

### Post by flash2lightning on 2006-12-02
thank you so much taurus, muchas gracias, it works

---

### Post by taurus on 2006-12-02
Good.

---

