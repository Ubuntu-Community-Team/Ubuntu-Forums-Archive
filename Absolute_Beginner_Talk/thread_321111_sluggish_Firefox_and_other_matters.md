---
title: "sluggish Firefox and other matters"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by venik212 on 2006-12-18
I have several questions:
1) I have installed Ubuntu without a hitch.  But Firefox on it is EXTREMELY slow, and many sites time out before I get what I needed.  Where do I find settings for the tcp/ip stuff and network connections in general??
2) Downloaded the Lyx bundle, but it is unclear how to install it.
3) Downloaded Thunderbird, but how do I install it?
4) How do I change screen resolution on my monitor?

Thanks for your help,

---

### Post by taurus on 2006-12-18
1.  ```
ifconfig
```

2.  ```
sudo aptitude update
sudo aptitude install lyx
```

3.  ```
sudo aptitude install mozilla-thunderbird
```

4.  ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by angkor on 2006-12-18
> **venik212 said:**
> 
2) Downloaded the Lyx bundle, but it is unclear how to install it.
3) Downloaded Thunderbird, but how do I install it?


It's easier to use the package manager for these programs then it is to download and install them manually. You can use Synaptic (System -> Administration) to install Lyx and Thunderbird or use the terminal:

```
sudo apt-get install lyx mozilla-thunderbird
```

You will be prompted for your user password. For further reading, check this out:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by venik212 on 2006-12-18
Thanks-- this has been VERY helpful, and super fast!

---

### Post by venik212 on 2006-12-18
Every time I type this sudo aptitude update (it's all UBUNTU to me..) I am told it is connecting to ubuntu security etc, where it gets stuck for a long time.  Do they keep a detailed list of what I have?

---

