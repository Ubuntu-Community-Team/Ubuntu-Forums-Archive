---
title: "Download Manager that able to do ppp0 reconnect"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by wadehel on 2006-09-22
I have weird ISP here, it get idle in randomly manner (still connected but no data received) so i need to disconnect ppp0 then reconnect again to continue the download proccess. Its painful because i have to check the pc very often.

I think the feature i needed will be like this:
If there is no n Byte of data received in n seconds then do ppp0 disconnect, then do ppp0 connect again, then resume the download.

In windows xp im using combination of flashget(download manager) and gprs counter (DU-Meter like software that do reconnect when condition met).

Question:
Is there any download manager that able to do that kind of action in Ubuntu? I tried DownThemAll in firefox but it cant do ppp0 action i need.

Thankyou

---

### Post by croak77 on 2006-09-22
I think kget does that. Not sure if d4x does.

---

### Post by wadehel on 2006-09-23
Thankyou, i tried d4x after your post, it is a very good downloader. But it cant do auto ppp0 reconnect.

Maybe i need some dialer script to do this :-?

---

