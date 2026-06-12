---
title: "Many questions"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by danieltowsey on 2006-12-15
I just reinstalled ubuntu..I am now 'oem' user...what should I do next? Should I start installing programs in add remove or should I do that after I 'sudo oem-config-prepare" ? I have alot of other customizing I want to do..should I them after too?

---

### Post by hyper_ch on 2006-12-15
What do you mean by "oem"?

---

### Post by danieltowsey on 2006-12-15
Thats sounds like an odd question..have you ever installed Ubuntu? I am not trying to be ignorant...

---

### Post by Bachstelze on 2006-12-15
Most people don't know about he OEM installation because it's not meant to be used by the end user (like you and me). If you have done an OEM instalation, you must run the part that is supposed to be run by the end-user, which is described [here](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview).

---

### Post by jonesyp on 2006-12-15
Just read last comment

[http://en.wikipedia.org/wiki/Original_equipment_manufacturer]("http://en.wikipedia.org/wiki/Original_equipment_manufacturer")

---

### Post by Bachstelze on 2006-12-15
> **jonesyp said:**
> Where did you gey your CD from.  OEM mean original equipment manufacturer, you do not get that in an Ununtu install!! 

For your information, there is an OEM installation of U**b**untu since Dapper. See the link I posted above.

---

### Post by danieltowsey on 2006-12-15
> **HymnToLife said:**
> Most people don't know about he OEM installation because it's not meant to be used by the end user (like you and me). If you have done an OEM instalation, you must run the part that is supposed to be run by the end-user, which is described [here](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview).
actually after it installed it said I would only be able to log in as 'oem' user then do all the changes I need then run 'sudo oem-config-prepare'

---

### Post by danieltowsey on 2006-12-15
> **danieltowsey said:**
> actually after it installed it said I would only be able to log in as 'oem' user then do all the changes I need then run 'sudo oem-config-prepare'
I checked out the link..theres only one thing that was different. when I went to install the two top chooses were "text or oem" to me oem means original equipment manufacture" so I just picked it...I will now run the sudo command thanks

---

### Post by taurus on 2006-12-15
Log in with oem username and password that you have created.  At the prompt, run

```
sudo oem-config-prepare
```
It will create a user account for you with sudo enable (since you were having problem with it the last time) and remove oem at the same time...

---

### Post by Sef on 2006-12-15
For those who wonder what OEM means: OEM stands for Original Equipment Manufacturer.  If you are building computers, then you might have a need for it.  Otherwise, just use text, the default option.

---

