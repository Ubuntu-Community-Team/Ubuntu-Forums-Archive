---
title: "using ssh , telnet server account"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-10-15
hi,
 i have a free shell account. how can i use it in my kubuntu?
i am new to shell accounts. plz tell me if i need some software or not.

---

### Post by taurus on 2006-10-15
Open a terminal and do

```
ssh -l <username> <IP Address>
```

---

### Post by u04f061 on 2006-10-15
> **taurus said:**
> Open a terminal and do

```
ssh -l <username> <IP Address>
```
ip address of what? should i give ip address of my internet provider or the server to which i am connecting.

---

### Post by taurus on 2006-10-15
The IP address of the server that you want to connect to!!!  

```
man ssh
```

---

### Post by u04f061 on 2006-10-15
but the server has given me url only. it has not given me any ip address

---

### Post by taurus on 2006-10-15
Then I guess you have to log in using a web browser.  What is the url of your server then?  Maybe I can look it up and give you the IP adress...

---

### Post by u04f061 on 2006-10-15
> **taurus said:**
> Then I guess you have to log in using a web browser.  What is the url of your server then?  Maybe I can look it up and give you the IP adress...

they sent me an email whose main points are 


  " Your new shell account is ready to use.
Hostname of the server is catcher.no-ip.org "

after this they gave me an id and password. nothing else

---

### Post by u04f061 on 2006-10-15
ok i have got the ip address of my server here it is the command 

   ejaz@ejaz:~$ ssh -l u04f061 83.240.4.187
it got nothing output even in 3 minutes i waited.

---

