---
title: "help me configure my internet connection"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Nedux on 2007-10-23
hi there `, I need to know how to configure my internet connection before installing ubuntu `.
Is is it possible to do this by running ubuntu from a live cd `?
i`m have  integrated intel pro/100 VE Network Connection.

---

### Post by scrooge_74 on 2007-10-23
Yes, try it with the Live CD

The changes wont stick after you shut down but you should be fine using it duringa Live session

---

### Post by Nedux on 2007-10-23
ok` , but how can I do that ,` is mi first time when I use linux, and i really like, hmm ... if I will fix this issue  I will install it.

---

### Post by Nedux on 2007-10-23
[IMG]http://www.mariusnedelcu.com/prscreen.jpg[/IMG] hei people `, I would realy need some help here `, this are my internet connection properties 

I also have a username and password , please people help me configure this internet connection so I can get rid of this fu**ing  windows.`

I tried to go to applications>internet>network terminal, done some settings there but didn`t work . I think there`s some other way to configure internet connection.

---

### Post by ItsMitsHere on 2007-10-23
go to terminal (applications>accesories>terminal) and type 
**sudo pppoeconf**
hit enter, then follow the onscreen instructions. if you dont know anything, follow default options. when the blue screen asks for user name, hit back-space until the user_name is deleated and then type your user name, hit enter and it will ask for your password. give it the password. again follow instructions untill it finishes. it will connect automatically first time.

then next time onwords to connect type in terminal **pon dsl-provider** and to see the connection log type **plog** and to disconnect **poff dsl-provider** 

post back if any problems.

---

### Post by Nedux on 2007-10-23
thanks man `:D it realy works `,:D right now i`m connected by using ubuntu live cd ` :D
hmm one more issue before installing , i made a backup folder on d: I hope I wonnd`t loose any data in that folder ,. is it safer to burn it on dvds `?

you prbably can`t imagine how happy I am that I have this internet connection running on ubuntu `:D

---

### Post by scrooge_74 on 2007-10-23
You can burn to a dvd and can make that disk availble in windows with read/write permits using ntfs-3g

[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+driver+install](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+driver+install)

---

### Post by ItsMitsHere on 2007-10-24
> **Nedux said:**
> thanks man `:D it realy works `,:D right now i`m connected by using ubuntu live cd ` :D
hmm one more issue before installing , i made a backup folder on d: I hope I wonnd`t loose any data in that folder ,. is it safer to burn it on dvds `?

you prbably can`t imagine how happy I am that I have this internet connection running on ubuntu `:D

further you can make a launcher to start internet on desktop (ask me how to if you dont know) enjoy!

if you are not going to make installation on D drive then you wont mess up anything. just remember to partition your hd manually while installing...

As for the last line, i really can imagine how happy u are by connecting to internet with command line. its really amazing!!! it still fascinate me...

---

