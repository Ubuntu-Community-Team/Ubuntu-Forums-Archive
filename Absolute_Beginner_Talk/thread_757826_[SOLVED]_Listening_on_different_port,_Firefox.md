---
title: "[SOLVED] Listening on different port, Firefox"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-04-17
Hi,

I installed apache and would like to let it listen on another port than 80. Does anybody know how to configure Firefox to listen on a specific port when accessing a certain IP address?

Thx,
Ben

---

### Post by Oldsoldier2003 on 2008-04-17
> **ben22 said:**
> Hi,

I installed apache and would like to let it listen on another port than 80. Does anybody know how to configure Firefox to listen on a specific port when accessing a certain IP address?

Thx,
Ben

url   :  port

for example  [http://www.someplace.com:8080](http://www.someplace.com:8080)

---

### Post by mick8985 on 2008-04-17
I doubt its possible, being a web browser 80 will be default. It may be possible to make firefox listen to a different port for all websites, but I doubt it can be set for specific websites. There may be a plugin that does redirects for certain web addresses, but a cursory search I did doesn't seem to show up with anything. Why do you want to do this?
> "url : port

for example http://www.someplace.com:8080"
I presumed you knew this and wanted a tool to automatically do it for certain web addresses

---

### Post by Borbus on 2008-04-17
I don't think you can configure firefox to listen on a certain port. Clients just pick a random high port to listen on. You can make Firefox connect to a different port by using the url:port syntax, though.

---

