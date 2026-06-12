---
title: "Ahh!  Firefox won't start"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Mr. Matt on 2006-11-06
Earlier today I was trying to install Chinese input by following some of the instructions in other threads on this forum and installing SCIM.

Now firefox won't start up.  When I click on it, it says "Starting firefox" in the toolbar but that goes away and nothing happens.  I have tried re-installing SCIM and firefox but it is still the same.  I'm not sure if the problem has to do with SCIM as after I installed it I logged out of Ubuntu (Ctrl+Alt+Backspace) with firefox opened and after that it didn't work.  However the Quality Feedback agent loaded after that.

If I go to System Monitor I see that the process "firefox" is running but again, the program doesn't work.

I have Firefox 2.0 installed.

I would try completely uninstalling SCIM and firefox but it says they both depend on ubuntu-desktop which sounds pretty important and I don't want to remove that.

Thanks for any help in solving this.  Without being able to use firefox I can't do much.  (I am typing this from another computer).

---

### Post by angkor on 2006-11-06
Do you get an error when you start firefox from the terminal?

---

### Post by Mr. Matt on 2006-11-06
Yes, I get:

```
/opt/firefox/run-mozilla.sh: line 131: 5819 Segmentation fault   "$prog" ${l+ "$@"}
```

---

### Post by Mr. Matt on 2006-11-06
Any suggestions or should I re-install Ubuntu?

---

### Post by taurus on 2006-11-06
Is that Dapper or Edgy?  And by the way, removing ubuntu-desktop is not going to cause a big melt down on your machine...

---

### Post by Mr. Matt on 2006-11-06
It's Dapper.  Hmmm..ok, maybe I will try to completely remove it and then install again.

---

### Post by taurus on 2006-11-06
> **Mr. Matt said:**
> It's Dapper.  Hmmm..ok, maybe I will try to completely remove it and then install again.
Read this...

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Mr. Matt on 2006-11-06
Thanks.  I ended up removing Firefox 2.0 according to the instructions.  Firefox 1.5 worked again but not Firefox 2 when I installed again.  So since my installation of Ubuntu was fairly new, I reinstalled it again.  I think I'll stay with Firefox 1.5 for the moment until I get other things sorted out.

---

### Post by Abiezer on 2006-12-04
FWIW, I think it is SCIM that causes the seg fault. I found installing the 'scim-bridge' package from the repositories, then adding this line ```
GTK_IM_MODULE=scim-bridge
``` to the very beginning of the FF start-up script (in my case /opt/firefox/firefox) means I can use FF 2.0 under Dapper, and enter Chinese too.

---

