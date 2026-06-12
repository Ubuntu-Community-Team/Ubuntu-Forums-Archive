---
title: "[SOLVED] Add program to startup file"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-02-25
Hi when i add Firestarter to the startup file via System>Preferences>Sessions >Startup Programs it ask you to enter the  command to run the program.

I entered Firestarter then when i re-boot i get a message stating firestarter needs priv. what would be the command to enter firestarter in the startup file ?

Thanks

---

### Post by John.Michael.Kane on 2006-02-25
firestarter is just an iptables front end which you already know. it starts up automatic at boot.

---

### Post by kent41 on 2006-02-25
Thanks for the info.

 I found a post that explains it very well, the following steps are.

1. Open a terminal and type:   

 ```
sudo gedit /etc/sudoers
```

2. and in the file that opens, add to the very last line (replacing "username" with your login name):

```
username ALL= NOPASSWD: /usr/sbin/firestarter
```

3. BE SURE TO REPLACE "username" WITH YOUR LOGIN NAME. now save the file and close it.

This will allow you to run the firestarter program with the sudo command without having to type in your password.

4.  The last step is to get** firestarter to boot at startup.**

    Click on Applications > System > Preferences > Sessions
    And click on the "Startup Programs" tab.
     Click "+ Add"  and paste

    ```
sudo firestarter --start-hidden
```

The post is 

[http://www.ubuntuforums.org/showthread.php?t=129798&highlight=firestarter](http://www.ubuntuforums.org/showthread.php?t=129798&highlight=firestarter)

It works great  Thanks much

---

### Post by Diego De Rosa on 2007-06-12
> **kent41 said:**
> Thanks for the info.

 I found a post that explains it very well, the following steps are.

1. Open a terminal and type:   

 ```
sudo gedit /etc/sudoers
```

2. and in the file that opens, add to the very last line (replacing "username" with your login name):

```
username ALL= NOPASSWD: /usr/sbin/firestarter
```

3. BE SURE TO REPLACE "username" WITH YOUR LOGIN NAME. now save the file and close it.

This will allow you to run the firestarter program with the sudo command without having to type in your password.

4.  The last step is to get** firestarter to boot at startup.**

    Click on Applications > System > Preferences > Sessions
    And click on the "Startup Programs" tab.
     Click "+ Add"  and paste

    ```
sudo firestarter --start-hidden
```

The post is 

[http://www.ubuntuforums.org/showthread.php?t=129798&highlight=firestarter](http://www.ubuntuforums.org/showthread.php?t=129798&highlight=firestarter)

It works great  Thanks much

If you edit sudoers file with sudo you mess up things! at least with ubuntu 7.04 I experienced a problem after doing so! There's command visudo for that... I'll go and give a look at manual...

---

