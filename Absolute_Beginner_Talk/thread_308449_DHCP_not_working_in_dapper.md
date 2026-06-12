---
title: "DHCP not working in dapper"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by apral on 2006-11-28
Want to sell a couple of computers with dapper on them to help spread the word but with DHCP not working it would only produce complaints.No updates I have found so far resolve the issue & most punters won't accept the trouble of manually configuring their internet connection.Is there something basic I'm missing?:rolleyes: With everything else working so well it's such a small but apparently important thing:confused:

---

### Post by meborc on 2006-11-28
have you tried

```
sudo dhclient
```

...you need to be connected to the internet ofcourse... what is the output in terminal after that command?

---

### Post by apral on 2006-11-28
I have my internet connection working but the only way I could do it was to phone my isp & get their dns & static ip address then enter them manually.This is the issue I want to address.I was only able to do this because of the help at launchpad.Most people used to windows won't want to have the trouble.I guess what I'm after is confirmation that I wasn't wrong to expect dhcp to make the internet connection easy & straightforward & since it made it harder than I expected if I can repair it for other users I might expose to Ubuntu?:)

---

### Post by apral on 2006-11-28
I"ve been reading more threads & it seems to be a continuing theme.It seems that it is important to enter the static address for your isp & make sure there is only one entry in the dns box at system-administration-networking.Persistance pays off so I will keep searching for a more palatable solution.:)

---

