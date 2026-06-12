---
title: "i ruined firefox putting java"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by esva on 2008-04-03
I ruined firefox i think!
I tried to install java manually (cause I couldn't chat) so I followed the instructions on the java page. I put the java folder in home though, cause I couldn't make it in usr how the page said. Then i supossedly created a virtual link in the terminal. But, maybe I shouldn't have made that cause I just know how to move around the terminal!
:(
Now firefox opens and at any request, it closes. Like If I try to go to any page, it closes inmediately. I thought maybe I could erase the link in that usr folder, but supossedly one can't do these things on those folders. I thought also on just erasing the java folder in home but I don't know if that would make it worse, how could I fix this?

---

### Post by privaterolf on 2008-04-03
To delete folders in directories that won't let you delete, run:

```
sudo nautilus
```

And that should let you delete it.

Haven't ever run into this problem, though.  So be careful.

---

### Post by esva on 2008-04-03
i deleted the folder(the java thing is my home flder) and the browser opens even though the idea of the weird link being there distuirbs me.

---

### Post by stchman on 2008-04-03
> **esva said:**
> I ruined firefox i think!
I tried to install java manually (cause I couldn't chat) so I followed the instructions on the java page. I put the java folder in home though, cause I couldn't make it in usr how the page said. Then i supossedly created a virtual link in the terminal. But, maybe I shouldn't have made that cause I just know how to move around the terminal!
:(
Now firefox opens and at any request, it closes. Like If I try to go to any page, it closes inmediately. I thought maybe I could erase the link in that usr folder, but supossedly one can't do these things on those folders. I thought also on just erasing the java folder in home but I don't know if that would make it worse, how could I fix this?

You can install Java from Synaptic.  No need to manually install it.

Try deleting the ~/.mozilla folder.

---

### Post by forrestcupp on 2008-04-03
If it still doesn't work after removing your Java files/folders and deleting your /.mozilla folder, you could try doing a 
```
sudo dpkg-reconfigure firefox
```
It might work.

Just some advice.  Before you install *anything* manually, check the forums and see if there is a good solution from the repos.  You can easily install Java like this
```
sudo apt-get install sun-java6-plugin
```

---

