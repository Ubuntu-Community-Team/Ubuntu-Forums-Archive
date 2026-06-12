---
title: "dial up internet problems"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Daneel42 on 2007-03-16
OK. I have AT&T worldnet service and I have been trying to set up my internet connection for days now. I'm using wvdial. I've set up the wvdial.conf file and the CHAP-secrets file and it is still not connecting. My ISP isn't compatible with gnome ppp so wvdial is the best option. The phone dials so I know my modem is configured correctly. The problem occurs a few seconds after it dials when wvdial reports that the ppp daemon has just died (exit code 16). I haven't yet figured out what this means or how to fix it. Any ideas?

---

### Post by terdon on 2007-03-17
OK, first of all the error code. If you do ```

man pppd
```
you will see near the bottom of the man page a list of the error codes and their (short) explanations:
> 16     The link was terminated by the modem hanging up.

This sounds like your /etc/wvdial.conf file is not set up correctly. Could you post the output of 
```
 cat /etc/wvdial.conf
```

---

### Post by Daneel42 on 2007-03-20
ill get u that info as soon as i reinstall ubuntu

---

