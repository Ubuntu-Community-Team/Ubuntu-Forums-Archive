---
title: "Port use in ubuntu"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-13
Hello people , 
              I am faced with the following are the issues that i am having :

1] How do i find out which TCP and UDP ports are being used on my ubuntu machine ( i know that /etc/services file has the list of port numbers , so i want to know wheter a particular service is using that particular port number at a given time )

2] If i find that a service is using a particular port number and i want to stop its usage , how do i go about doing it .

Thanks in advance, 
Lance

---

### Post by ciscosurfer on 2006-12-13
> **lance_klusener said:**
> Hello people , 
              I am faced with the following are the issues that i am having :

1] How do i find out which TCP and UDP ports are being used on my ubuntu machine ( i know that /etc/services file has the list of port numbers , so i want to know wheter a particular service is using that particular port number at a given time )

2] If i find that a service is using a particular port number and i want to stop its usage , how do i go about doing it .

Thanks in advance, 
LanceGo to a terminal, and enter in **man netstat**.

---

### Post by goatflyer on 2006-12-13
```

netstat -tln

```
will show you all the port numbers that are being listened to.  Ports below 1024 are 'well-known' services.  But with Ubuntu, if you haven't explicitly enabled any services yourself, it doesn't either.

```

netstat -tl

```

will attempt to translate port number into well-known name, it will give you a hint of what service is running.

Hope this helps.

---

### Post by lance_klusener on 2006-12-13
Yes i got these commands , the thing is there are some services that are running on some ports which i want to stop so that i can restart them manually again ( these services were started by a script automatically when the machine rebooted )

Thanks for your replies,
Lance

---

### Post by xabbott on 2006-12-13
Which services do you need to stop?

---

### Post by lance_klusener on 2006-12-14
I have installed sun n1 grid on my ubuntu , but while installing i have enabled auto start of the server , this causes the ports 6444 and 6445 to be in use when my machine starts . 

So i want to get those ports free and restart the services manually.

Thanks

---

