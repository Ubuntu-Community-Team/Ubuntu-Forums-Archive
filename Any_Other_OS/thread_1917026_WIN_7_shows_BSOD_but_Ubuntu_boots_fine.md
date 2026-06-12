---
title: "WIN 7 shows BSOD but Ubuntu boots fine"
date: 2012-01-29
forum: Any Other OS
---

### Post by linuxyogi on 2012-01-29
Hi,

I have a PC which boots Ubuntu fine but shows Blue Screen of Death while booting to WIN 7.

AFAIK BSOD happens due to hardware issues. So I was curious how is Ubuntu working ? (And not WIN 7)

---

### Post by sffvba[e0rt on 2012-01-29
BSOD is not necessarily a hardware issue (as you can observe yourself now first hand).


404

---

### Post by sffvba[e0rt on 2012-01-29
*Thread moved to **Other OS/Distro Talk**.*


404

---

### Post by terry_gardener on 2012-01-29
i suspect that it is a driver issue try and boot into safe mode uninstall the offending driver or roll back to when it worked.

as the above person says it cant be HW related due to ubuntu working.

---

### Post by linuxyogi on 2012-01-29
> **terry_gardener said:**
> i suspect that it is a driver issue try and boot into safe mode uninstall the offending driver or roll back to when it worked.

as the above person says it cant be HW related due to ubuntu working.

I have installed only the sound driver. Uninstalling it will stop sound from working. I dunno what to do.:confused:
Also, the BSOD doesn't appear on every boot. Sometimes it boots fine.

---

### Post by haqking on 2012-01-29
> **linuxyogi said:**
> I have installed only the sound driver. Uninstalling it will stop sound from working. I dunno what to do.:confused:
Also, the BSOD doesn't appear on every boot. Sometimes it boots fine.

note down the hex error code associated with the BSOD and search for it.

[http://technet.microsoft.com/en-us/library/cc750081.aspx](http://technet.microsoft.com/en-us/library/cc750081.aspx)

[http://pcsupport.about.com/od/findbyerrormessage/tp/stop_error_list.htm](http://pcsupport.about.com/od/findbyerrormessage/tp/stop_error_list.htm)

A BSOD is a generic term for many possibilities which are communicated to you with a stop (error) code displayed on the screen.

Cheers

---

### Post by wolfen69 on 2012-01-29
[http://www.sevenforums.com/tutorials/1538-sfc-scannow-command-system-file-checker.html](http://www.sevenforums.com/tutorials/1538-sfc-scannow-command-system-file-checker.html)

---

### Post by linuxyogi on 2012-02-01
> **terry_gardener said:**
> i suspect that it is a driver issue try and boot into safe mode uninstall the offending driver or roll back to when it worked.

as the above person says it cant be HW related due to ubuntu working.

> **haqking said:**
> note down the hex error code associated with the BSOD and search for it.

[http://technet.microsoft.com/en-us/library/cc750081.aspx](http://technet.microsoft.com/en-us/library/cc750081.aspx)

[http://pcsupport.about.com/od/findbyerrormessage/tp/stop_error_list.htm](http://pcsupport.about.com/od/findbyerrormessage/tp/stop_error_list.htm)

A BSOD is a generic term for many possibilities which are communicated to you with a stop (error) code displayed on the screen.

Cheers

> **wolfen69 said:**
> [http://www.sevenforums.com/tutorials/1538-sfc-scannow-command-system-file-checker.html](http://www.sevenforums.com/tutorials/1538-sfc-scannow-command-system-file-checker.html)

I searched the hex error code & it seems like a display driver issue. I am atm downloading the latest driver for my card. Let's hope this will solve the issue.

Thanks to all for your replies.

---

### Post by TeamRocket1233c on 2012-02-02
Have you maybe tried reinstalling Win7 to see how that goes?

---

### Post by linuxyogi on 2012-02-03
> **TeamRocket1233c said:**
> Have you maybe tried reinstalling Win7 to see how that goes?

After installing the updated display driver I haven't received the error. I guess the issue is solved.

---

