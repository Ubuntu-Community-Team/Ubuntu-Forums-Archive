---
title: "command 'make' is invalid"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by vivin_west on 2006-12-01
I am trying to get a printer started visited a ubuntu forum where this command is used. But when I try it it is not working. Please help.

---

### Post by Bachstelze on 2006-12-01
Sorry, my crystal ball is currently under maintenance so please provide more details about the error you get.

---

### Post by vivin_west on 2006-12-01
I am trying to install a HP laser printer and posted a help request an hour back.No one answered.So I searched some previous threads in your forums and found how to install the printer.In that instructions he uses a command called make. When I type the same command it gives a 'invalid command' message. I want to know how to proceed

---

### Post by Bachstelze on 2006-12-01
```
sudo apt-get install build-essential
```

---

### Post by freebeer on 2006-12-02
At the risk of confusing you even more...

The 'make' command is a compiler command.  Presumably the instructions you're been reading are related to building from source code.  The error is due to the fact that you probably don't have the compiler installed.

The instructions given above will install the necessary files onto your system so that you will then be able to compile and **make** the item.

Hope that helps some.

---

### Post by deadgobby on 2006-12-02
just a silly question. What HP laser printer are you trying to install?
Gobby

---

