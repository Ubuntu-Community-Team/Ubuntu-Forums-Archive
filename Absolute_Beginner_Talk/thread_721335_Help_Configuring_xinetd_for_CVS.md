---
title: "Help Configuring xinetd for CVS"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by DaddyUnit on 2008-03-11
I'm a new Linux/Unbutu user trying to install CVS. I'm trying to follow instructions I found at this post [https://help.ubuntu.com/7.04/server/C/cvs-server.html](https://help.ubuntu.com/7.04/server/C/cvs-server.html). I THINK I've managed to install CVS and xinetd and am at the step where I'm supposed to be configuring xinetd by adding text/code to the "/etc/xinetd/cvspserver".

I can't find anything called "/etc/xinetd/cvspserver". I can't find this directory/file. I did find similar text/code in a file "/etc/xinetd.d/chargen" and tried to modify it but got an error when I tried to save the file saying that I didn't have the permissions necessary to save the file.

Is the reason I don't have an /etc/xinetd.d directory and not a /etc/xinetd directory because I've got a different/newer version of xinetd or am I just not looking in the right place. Should I be looking for a cvspserver file? Is this a file I need to create?

Any help would be greatly appreciated.

Thanks

---

### Post by Cypher on 2008-03-11
You can create the cvspserver file in the /etc/xinetd directory and the it should get found and used by the Xinetd daemon when it starts up.

Now mind you, you don't specifically need Xinetd, you can always start the CVS server and have it running all the time. Xinetd mainly provides the capabilty of starting/stopping the CVS server on-demand..

---

### Post by DaddyUnit on 2008-03-11
Thanks for your response.

Do you think the /etc/xinetd.d directory is the same as the /etc/xinetd directory? (I don't have an /etc/xinetd directory).

If I don't need the xinetd maybe I'll skip it for now until I can "get a clue".

Thanks for your help.

---

### Post by DaddyUnit on 2008-03-11
...Still searching for a clue.

I've been searching for documentation on how to install and run CVS on Unbutu/Linux. I've come up with a small handful but none of them talk about how to start or stop CVS service. I'm pretty sure I've installed CVS (when I go to synaptic it won't let me re-install it) but have no idea how to get it going. If anyone has a link for instructions on how to do this I'd really appreciate it.

Thanks

---

### Post by Cypher on 2008-03-12
You might have better luck with the [instructions]("http://sanatio.blogspot.com/2005/12/cvs-server-on-ubuntu.html") on this page. It skips XINETD all together and runs CVS standalone.

---

### Post by Astas on 2008-04-11
> **DaddyUnit said:**
> Thanks for your response.

Do you think the /etc/xinetd.d directory is the same as the /etc/xinetd directory? (I don't have an /etc/xinetd directory).

If I don't need the xinetd maybe I'll skip it for now until I can "get a clue".

Thanks for your help.


You may be reading the documentation for the older 7.04 version which refers to /etc/xinetd.

In 7.10 it is /etc/xinetd.d - I came across the same issue

---

