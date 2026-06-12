---
title: "auto login and auto start"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by My_Ausweis on 2008-03-14
Dear All

How can i log ubuntu without username and password (auto login) 

can i start firestarter automaticaly (without go to menu first) when i turned on computer ?

Thx

L.M

---

### Post by kpkeerthi on 2008-03-14
System -> Admin -> Login Window -> Security -> Enable Auto Login

Add 
```

/etc/init.d/firestarter start

```
to the file /etc/rc.local with gedit 
```
gksudo gedit /etc/rc.local
```

After login, check if firestarter is running using
```

/etc/init.d/firestarter status

```

---

