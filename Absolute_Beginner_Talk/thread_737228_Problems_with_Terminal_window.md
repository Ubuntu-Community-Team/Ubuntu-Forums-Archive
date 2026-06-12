---
title: "Problems with Terminal window"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by smallzoo on 2008-03-27
I am having problems with wireless networking so I wanted to try some hints from users in this site using the terminal window.

App/Accessories/Terminal..works fine opens a window

I can type ls then ENTER and it shows Desktop Examples and returns to the command line

BUT if I try one of the suggested commands such as 

sudo cat /etc/network/interfaces
or
sudo apt-get update 

and hit ENTER it just goes to the next line and does nothing..

any clues

---

### Post by ahsile on 2008-03-27
what's the output of: ifconfig

(note, no need to sudo)

---

### Post by smallzoo on 2008-03-27
Hi there.. the same

at the $ prompt if I type ifconfig and hit enter the cursor moves to the next line and then just sits there!

---

### Post by ahsile on 2008-03-27
Very strange. It's almost as if the stdout is being directed somewhere else by default. I think you're beyond my level of expertise on this one :(

---

### Post by smallzoo on 2008-03-27
Thanks anyway. as I sais I can type ls and hit enter and it shows the directory I am in but not ifconfig etc.. anyone you suggest I talk to or maybe another forum group ?

Thanks

---

### Post by mali2297 on 2008-03-27
Try in order
```

ls
cat /etc/network/interfaces

```
Same behaviour? (That is, the first command works but not the second.)

---

### Post by smallzoo on 2008-03-27
Thanks.

That works.. I get

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wpa-driver wext
wpa-key-mgmt wpa-psk
wpa-proto wpa2
wpa-ssid GEN-Wireless

auto wlan0

How to I now edit the interfaces ?

Thanks

---

### Post by mali2297 on 2008-03-27
Now try
```

sudo network-admin

```
You should be asked for a password, just type it and press Enter. You won't get any visual feedback as you write the password but the system still reads what you type.

Do you get any errors?

---

### Post by ahsile on 2008-03-27
I'm wondering... did you accidentally put a single (') or double (") quote on a line in the terminal? If you do that it will keep accepting lines and do nothing until you enter the matching quote or hit CTRL-C.

---

### Post by smallzoo on 2008-03-27
No but this line and the network window works when I dont have the wireless card in. As soon as the network card is plugged in the commands dont work

---

### Post by smallzoo on 2008-03-27
Thanks for everyone's help..

I used sudo mousepad to remove all entries in the interfaces file and then added the wireless card again.

Thanks

---

### Post by mali2297 on 2008-03-27
> **smallzoo said:**
> 
Thanks for everyone's help..

I used sudo mousepad to remove all entries in the interfaces file and then added the wireless card again.

Thanks

I'm glad that it worked out for you. Just a small note..

When opening graphical applications like Thunar or Mousepad, it is advisable to use **gksu** instead of sudo.

```

gksu mousepad 

```

---

### Post by smallzoo on 2008-03-28
Thanks

---

