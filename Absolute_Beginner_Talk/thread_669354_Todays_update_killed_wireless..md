---
title: "Todays update killed wireless."
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2008-01-16
There was a kernel update included in todays updates. Upon re-boot, wireless was gone. 

It was under eth1, but now, that option is gone under networking and network tools. 

ndiswrapper -l shows my driver is installed and good. iwconfig doesn't list eth1 anymore. I don't remember what it showed under ifconfig.

It's an older Dell laptop, but I know there are a lot of us here using these. Mine's a dell lattitude c610
 Any help would be appreciated!

---

### Post by eolson on 2008-01-16
Do you have internet at all xxx like wired?

---

### Post by Papa-san on 2008-01-16
Right now I am running under the old kernal, so I have it. I will have to move it and run my cat5 to use the new one.

---

### Post by Rotaj on 2008-01-16
Do you have the grub menu available at boot? If so, just boot to the previous kernel.

I know this is not the answer that you were looking for, but hopefully this should act as a workaround until the right solution presents itself.

---

### Post by eolson on 2008-01-16
here's what I did xxxx
   uninstalled and then reinstalled the ndiswrapper.   Didn't mess with the driver.
wirless is working again.

---

### Post by Papa-san on 2008-01-16
OK. Thanks.

What would the proper commands be to do this?

---

### Post by Papa-san on 2008-02-18
Update Manager is prompting me to do this again. Does anyone know if this issue has been resolved yet? Just wondering if I should bother with trying it again...

---

