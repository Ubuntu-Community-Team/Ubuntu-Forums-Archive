---
title: "Can't access &quot;Documents&quot; folder"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by dseybert on 2007-06-28
So I am logged in to Linux as myself, Doug. There is a folder called /Home/Doug/Documents. I would think this is somewhat equivalent to the "My Documents" folder in Win****, right? So why do I need to be logged in as "root" to write any files to it? I look under the properties for the folder and it belongs to "root" instead of "doug". Am I missing something?

---

### Post by Najand on 2007-06-28
Open a terminal and type:
```

sudo chown doug:doug /home/doug/Documents

```
and press enter.

---

### Post by Atreus12 on 2007-06-28
Edit: in linux there is a difference between Documents and documents, and between Doug and doug. Everything is case sensitive. Change the commands to match the case on your computer.

That's strange, the permissions don't appear to be set correctly. Did you create the directory while logged in as root?

Pull up the terminal (applications->accessories->terminal) and enter the following code

```
sudo chown doug:doug -R /home/doug/Documents
```

that will change the ownership to your user. If you still have problems, you will need to set permissions

```
sudo chmod 766 -R /home/doug/Documents
```

This will change the permissions to (read, write, execute) (read, write) (read, write) for owner, group, and others respectively. 

The second command is probably not necessary, simply changing the ownership of the file to your own name should make it work.

-Andrew


edit: Dang, beaten to it ;)

---

### Post by dseybert on 2007-06-28
Thanks, the

sudo chown doug:doug -R /home/doug/Documents

code *seems* to have worked. As for creating the folder, I didn't... It was created upon installation of Ubuntu (technically I suppose this means I created it logged in as root).

Thanks for the help!

---

