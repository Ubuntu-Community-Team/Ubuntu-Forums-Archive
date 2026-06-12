---
title: "ADSL network user name / password"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by lennyjames on 2006-07-14
Hello everyone,
I am glad to say that my transition to Umbuntu has been almost painless. My home system is 100% Umbuntu and my home office 50% Ubuntu! :D Windows is almost out the...ahem...window!

When operating in Windows XP, I sometimes have to disconnect my ADSL connection and re-connect. I think this is more of the ISP's problem when the line drops. Where can I do this in Ubuntu? Also, where can I find place to enter my user name and password for the ADSL connection?

Thanks!

---

### Post by %hMa@?b&lt;C on 2006-07-14
to connect via DSL you need to enter the command (in the terminal/konsole)
```
sudo pppoeconf
```

---

### Post by MaximB on 2006-07-14
once you configure your adsl connection you won't need to connect/disconnect ever !!!
it's always connected...but you can change it if you like.
just type
"sudo pppoeconf"
enter **your** password and begin the configuration !

---

