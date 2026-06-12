---
title: "Madwifi Problems"
date: 2007-09-01
forum: Apple Intel Users
---

### Post by czechman86 on 2007-09-01
Hey All!

i recently bought a new macbook, core duo 2, and installed linux on it, but because of the newer chip set, the wifi wasnt working. i went over to the faq page and tried to install madwifi, but here is what i got:

```
@macbook:~$ wget http://snapshots.madwifi.org/madwifi-hal-0.9.30.13-current.tar.gz
--22:52:31--  http://snapshots.madwifi.org/madwifi-hal-0.9.30.13-current.tar.gz
           => `madwifi-hal-0.9.30.13-current.tar.gz'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:52:31 ERROR 404: Not Found.
```

The first step worked without any problems, but i cannot get the file off the server. i am aware that there are new madwifi drivers available, but do not know how to download them. i used ppc linux for a while, but quit for a long time, so i am new to all of this again. any help that you could offer would be greatly appreciated.

thanks a million!

---

### Post by pxwpxw on 2007-09-02
Try this:
[http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz)

---

### Post by czechman86 on 2007-09-02
thanks for the help, i downloaded the package, but now, i have run into another problem:

```
@macbook:~$ tar -zxvf madwifi<tab>
bash: syntax error near unexpected token `newline'
```

im very new at this, like i said, and so its probably a stupid error, but any help that you can provide is awesome. Dekuju kamarady!

---

### Post by pxwpxw on 2007-09-02
> **czechman86 said:**
> thanks for the help, i downloaded the package, but now, i have run into another problem:

```
@macbook:~$ tar -zxvf madwifi<tab>
bash: syntax error near unexpected token `newline'
```


You should enter

```
@macbook:~$ tar -zxvf madwifi
```
then you press the **tab key**, and it will complete the filename, then you hit the** enter key**.

---

### Post by czechman86 on 2007-09-02
Great success! the wifi is working without any problems!

thanks a million!

---

