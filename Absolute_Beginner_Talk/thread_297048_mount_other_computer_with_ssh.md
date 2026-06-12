---
title: "mount other computer with ssh"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-11-10
I still cannot understand this at all. Why cannot it be as easy as My Network Places on Windows? Not that that one works everytime, but still.

I have two computers here with server names
1) 192.168.1.64
2) 192.168.1.65

I want to get things from 2) to 1)

What do I do on computer 2) to make my home directory shared?

What do I do on computer 1) to get the stuff? When I go to "connect to server", it asks several things:
type - I choose ssh (I guess)
server - address of 2) - 192.168.1.65?
Port - ?
Directory - ?
username - ?
name to be used for connection - ?
(The questions are translated from my language, not necessarily correct)

I am so sorry to be asking specific questions like these, but I have tried several guides and I cannot understand anything.
I'll be so happy if I get some feedback suited for someone as ignorant as me.

---

### Post by echo $USER on 2006-11-10
Are the two hosts running linux or a mix of linux and windows?

---

### Post by 1002285 on 2006-11-10
> **echo $USER said:**
> Are the two hosts running linux or a mix of linux and windows?

Both have Ubuntu, 2) has Dapper and 1) Edgy.
(Both machines have Windows, too, and the home partitions can be read by windowses (ext3))

---

### Post by JShadow on 2006-11-10
You can use SSH but you must install the SSH daemon first. Ubuntu has a "no open ports" policy so it does not allow any connections by default.

To install SSH, in a terminal
```
sudo apt-get install openssh-server
```

Next, back to the dialog you're trying to fill out. You have the address. Port and directory can be left blank, the defaults will be fine so I would just ignore those. 

Username will be the name you use to login **on the computer you are connecting to**. If you try using the login information from the PC you are on, it won't work.

Name for the connection, is just what you want to save it as. "My other pc" or something like that.

Once you've filled that all out and hit ok, go back to the places menu and select the item you just created. It should prompt you for the password for the remote computer, same as what you use to login. Enter that and you should be looking at your files.

---

### Post by 1002285 on 2006-11-10
> **JShadow said:**
> You can use SSH but you must install the SSH daemon first. Ubuntu has a "no open ports" policy so it does not allow any connections by default.

To install SSH, in a terminal
```
sudo apt-get install openssh-server
```

Next, back to the dialog you're trying to fill out. You have the address. Port and directory can be left blank, the defaults will be fine so I would just ignore those. 

Username will be the name you use to login **on the computer you are connecting to**. If you try using the login information from the PC you are on, it won't work.

Name for the connection, is just what you want to save it as. "My other pc" or something like that.

Once you've filled that all out and hit ok, go back to the places menu and select the item you just created. It should prompt you for the password for the remote computer, same as what you use to login. Enter that and you should be looking at your files.

openssh-server has to be installed on both computers?

---

### Post by echo $USER on 2006-11-10
openssh-server only needs to be installed on the host you want to connect to.  ssh client is installed by default.

---

### Post by 1002285 on 2006-11-10
Thank you!
I guess the only thing I was missing the presious time I tried was openssh-server, I did try using all possible usernames.
I guess nobody in the forums understood how little I knew about this.
Thank you, I have the connection working now.

---

