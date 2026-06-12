---
title: "Slow internet"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by PFSpectrum on 2008-04-10
I just installed linux and i got my internet connection working... but the connection is really slow... on my vista partition the connection is fast... how do i fix this?

---

### Post by superprash2003 on 2008-04-10
it could be a DNS problem , changing to opendns servers may help..
go to your terminal and type
sudo gedit /etc/dhcp3/dhclient.conf
then add the following line to the end of the file

prepend domain-name-servers 208.67.222.222,208.67.220.220;

save the file and close it..this should make it faster

---

### Post by PFSpectrum on 2008-04-10
thanks it workded

---

### Post by dan-buntu on 2008-05-01
> **superprash2003 said:**
> it could be a DNS problem , changing to opendns servers may help..
go to your terminal and type
sudo gedit /etc/dhcp3/dhclient.conf
then add the following line to the end of the file

prepend domain-name-servers 208.67.222.222,208.67.220.220;

save the file and close it..this should make it faster

Hi. I'm having the same problem here. For instance, I went to start a download of a 50mb ATI driver from their website, and it was going about 20-30 kps, where as, from my mac laptop, it downloaded at about 150 kps.

I tried editing the conf file like you suggested, but it made things worse, as in there was no internet connection at all. I may have done it wrong.

Should the "prepend domain-name-servers 208.67.222.222,208.67.220.220;" be pasted after the existing semi colon? Should there be spaces? another comma?

Thanks very much for any help.

---

