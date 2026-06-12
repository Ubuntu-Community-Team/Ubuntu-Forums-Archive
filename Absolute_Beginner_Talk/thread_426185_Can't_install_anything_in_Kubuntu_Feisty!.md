---
title: "Can't install anything in Kubuntu Feisty!"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-28
I tried to install using the command line, Add/Remove Programs, and Adept, and Adept Updater but none worked. In Add/Remove Programs, I can't even tick the check box of installing an app. In Adept, I nothing happens whenever I click "request install." In the command line, no candidate version of the apps are found. In Adept, I could not fetch updates; it said, "There was an error downloading updates."

What is going on?

How do I fix this?

---

### Post by taurus on 2007-04-28
What apps are you looking for?

```
sudo aptitude update
sudo aptitude install package_name
```

---

### Post by wersdaluv on 2007-04-28
> **taurus said:**
> What apps are you looking for?

```
sudo aptitude update
sudo aptitude install package_name
```

After entering sudo aptitude update, I saw more programs in Add/Remove Programs that I can install. I tested Adept by installing Abiword and it worked. When I tried to install wlassistant in Adept and Add/Remove Programs, I still cannot install it. When I tried to install KNetworkManager in Add/Remove Programs and Adept, "There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages." 

Why can't I install KNetworkManager and wlassistant?

I also noticed that in Add/Remove programs, there were some apps that were grayed out so I cannot install them.

What could be going on? Why can't I install? How can I fix this?

---

### Post by taurus on 2007-04-28
Try to install it from a terminal so you would get a better error message if there is one.

```
sudo aptitude update
sudo aptitude install **program_name**
```

---

### Post by Nythain on 2007-04-28
wlassistant has always given me problems... do you happen to be running a nvidia  card do you??? if so did you manually install the drivers with the .run package from the site??? i know that when i used to do that, something about killing restricted modules ended up keeping me from updating a lot of stuff cause it would break my nvidia driver...

---

### Post by wersdaluv on 2007-04-28
I figured the solution out! Thanks to taurus!

I am not at home so I chose the server here in Indonesia thinking that it will make things better for me to choose a near server. I ran the installation in Konsole and found out that the server here in Indonesia has a problem. 

I just chose the Main Server as a source using Adept and now, I can install already! 

:KS 

Thanks taurus! :)

---

