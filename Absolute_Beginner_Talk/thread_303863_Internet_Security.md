---
title: "Internet Security"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by NewRubberSoul on 2006-11-20
How can I make sure that the information I send over the net is protected?  I know that security issues are very important in the linux community, but I'm confused about how to make sure that I'm not broadcasting personal info when I'm on the internet.  I'm on a wireless network, using Kubuntu's Wireless Assistant.  Should my connection be encrypted?  How do I do that?

Thank you in advance for any help. :confused:

---

### Post by daou on 2006-11-21
You should be using WPA (Wi-Fi Protected Access) on your wireless. Whether you will be able to use it depends on the WLAN provider. Some have support, others don't.

---

### Post by wieman01 on 2006-11-21
First of all, your local wireless network should be encrypted using with WPA-TKIP or WPA-AES. I recommend WPA-AEP which is generally referred to as WPA2.

Second, sending encrypted information over the Internet is a reasonable thing to do. Generally you achieve that using PGP or GPG... private/public key encryption. There are plugins available for all popular email clients such as Thunderbird. However, encryption is only possible if the party you are sending information to uses encryption as well & publishes his/her public key. You find tons of information on the web concerning this.

When connecting to web-pages & transmitting personal data, make sure the website supports SSL (HTTPS). Then your data are protected. 

The last thing would be making use of a proxy that enables you to surf anonymously, however, this does not protect your data but only hides your identity.

Best security measure is to be very considerate with what you send over the web. Remember: Everything that is sent over the Internet will never leave it again. Traces can be found basically everywhere. This does not only apply to the Linux community but to everyone using a computer that is connected. Responsible handling of personal data is critical for everyone of us.

---

