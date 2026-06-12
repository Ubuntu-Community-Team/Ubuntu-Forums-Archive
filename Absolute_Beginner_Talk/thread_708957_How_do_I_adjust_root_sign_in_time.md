---
title: "How do I adjust root sign in time"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by metalaxesucks on 2008-02-26
Hi everybody,
I absolutely love Ubuntu, however there is one thing that absolutely gets on my nerves - this would be the freaking default sign in time as root of 15 minutes, or so.
I want to adjust the time to about 5 minutes. This is because every time I update my computer, I have to restart my pc to sign out again - I do not want to wait 15 minutes to surf the web! (surfing as root could be dangerous). 
Thanks

---

### Post by Presto123 on 2008-02-26
Edit...Wow, n/m that's for terminal.

---

### Post by chris.a.barker on 2008-02-26
You should be using sudo to do updates?

Are you implying that you have set up a "root" user and you are logging in as root?

If I am totally off the mark let me know!

---

### Post by taurus on 2008-02-26
I am not sure I understand your situation.  When you want to update your machine, you just run

```
sudo apt-get update
sudo apt-get upgrade
```
and while it is being updated, you can do whatever else you want as a regular user.  Why do you have to reboot your machine just so you can surf the net?

---

### Post by Oldsoldier2003 on 2008-02-26
> **metalaxesucks said:**
> Hi everybody,
I absolutely love Ubuntu, however there is one thing that absolutely gets on my nerves - this would be the freaking default sign in time as root of 15 minutes, or so.
I want to adjust the time to about 5 minutes. This is because every time I update my computer, I have to restart my pc to sign out again - I do not want to wait 15 minutes to surf the web! (surfing as root could be dangerous). 
Thanks
you don't need to log in as root to do updates... run updates and installs using sudo on your admin user. ie sudo apt-get intstall <package> or run synaptic or update manager and it will ask you for your sudo password.

---

### Post by spiderbatdad on 2008-02-26
[http://ubuntuforums.org/showthread.php?t=183418&highlight=sudo+timeout](http://ubuntuforums.org/showthread.php?t=183418&highlight=sudo+timeout)

---

### Post by shad0w_walker on 2008-02-26
I think you don't quite understand the issue. The update programs run using sudo and allow temporary access as root. However unless you run something with sudo even during the timeout period you won't be running it as root.

---

### Post by Paqman on 2008-02-27
> **metalaxesucks said:**
> I do not want to wait 15 minutes to surf the web! (surfing as root could be dangerous). 
Thanks

Using sudo only elevates your privileges for *that command*, it doesn't elevate your whole session to root. You'd only be surfing as root if you'd launched your browser with "sudo firefox", for example.

---

### Post by metalaxesucks on 2008-02-27
Ok, maybe I don't fully understand what I am talking about.
Let me try to clarify
When I see the orange update icon in the upper right hand corner and it tells me there are updates ready for my computer, I click on the icon and then click on something like install updates.
It then ask for my password. After I punch in my password, I am able to run things that would normally require my password with out punching it in. For example, I am able to run synaptic package manager. I am able to do this for about 15 minutes or so. And then finally after about 15 minutes, it start asking for my password again if I try to run synaptic package manager.
Isn't it dangerous to surf the web during these 15 min?
Sorry I am amateur on Ubuntu

---

### Post by taurus on 2008-02-27
The short answer is no.  You can surf or do whatever else you want to do while you have synaptic open.

---

### Post by spiderbatdad on 2008-02-27
Feel free to adjust root password request timeout, as outlined in the link I posted above.

---

### Post by PurposeOfReason on 2008-02-27
That is perfectly acceptable. Gnome just stored your password for a little bit, you're only being root where you normally would (but just without a password). Firefox is still the normal users and it never does ask for your password.

---

### Post by chris.a.barker on 2008-02-27
No it is not dangerous. The reason why is because you would have to launch firefox using the command [code]sudo firefox[/code[ in order for it to be launched as root.

Cheers

---

### Post by metalaxesucks on 2008-02-27
Thanks everybody for your smarts.
Thanks spiderbatdad for the link, but it looks like I don't have to worry about it so much anymore.

---

