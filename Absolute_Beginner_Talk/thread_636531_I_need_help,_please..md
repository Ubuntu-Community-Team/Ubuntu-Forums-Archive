---
title: "I need help, please."
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by sgt_FRY_co0ker on 2007-12-09
Hi all, I'm new to linux/ubuntu and I just installed Gutsy Gibbon 7.10 on my PS3, but I can't get online using firefox. I greatly appreciate help on this matter please.

Thanks in advance for any and all help.

---

### Post by ItsMitsHere on 2007-12-10
go to terminal (applications>accesories>terminal) and type 

**sudo pppoeconf**

hit enter, then follow the onscreen instructions. if you dont know anything, follow default options. when the blue screen asks for user name, hit back-space until the user_name is deleated and then type your user name, hit enter and it will ask for your password. give it the password. again follow instructions untill it finishes. it will connect automatically first time.

then next time onwords to connect type in terminal **pon dsl-provider** and to see the connection log type **plog** and to disconnect **poff dsl-provider** 

Also go to [http://ubuntuforums.org/showthread.php?t=589932]("http://ubuntuforums.org/showthread.php?t=589932")

post back if any problems.

---

### Post by schmildo on 2007-12-10
does PPPoe config allow you to configure non-ppoe configurations also?

---

### Post by yimmmy on 2007-12-12
or u could just enable ur network and set it to automatic dhcp
1. click on the two little computers in the top right corner 
2. select manual connection
3. then select the ethernet connection and set it up so its automatic 
4. wait a few minutes 
5. surf using firefox

---

