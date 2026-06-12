---
title: "x forwarding"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Joseaa on 2007-05-02
Could anyone explain to me the difference between local x server and x forwarding ? Moreover, how can I setup my ubuntu box for x forwarding?

---

### Post by chili555 on 2007-05-02
A local X server is the server running on the machine you are running X on at the moment. If it were not running X, you would have a black screen with white letters. Could you email and surf the web? Sure! Could you see digital photos of your dog? No.

X forwarding is when you log into another machine, usually by ssh, and forward X windows back to your machine. As an example, I can ssh to my wife's Ubuntu machine: ssh -l sylvia -X 192.168.x.yzz. I get a command prompt. I can then issue a command that pops up an application running on her machine, but places the window on *my* machine. An example is the command *sol* or *opera*.

No special setup is required, although X must be running on both machines. There are X servers that can be installed for Windows.

---

### Post by Joseaa on 2007-05-02
An explanation can't get clearer than this. Thanks a lot :)

---

