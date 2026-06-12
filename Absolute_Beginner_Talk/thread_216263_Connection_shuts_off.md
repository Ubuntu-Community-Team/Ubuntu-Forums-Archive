---
title: "Connection shuts off"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by rboik on 2006-07-15
](*,) I have everything working and the modem dials in to the internet but when it goes to connect it shuts off. ](*,)

---

### Post by verbatim210 on 2006-07-15
it could be anything from your ISP down to your phone line down to your modem.  how do you know its ubuntu?

---

### Post by rboik on 2006-07-15
Because I am not having any trouble with any of that when I use Win Xp. I just think I don't have my dialer setup right yet.

---

### Post by HereInOz on 2006-07-15
Call your ISP and ask them to check the connection logs for your account.  That might give you a clue as to what is happening and when in the connection process the disconnection is happening.

Do you actually get a dial tone, then the dial up and the handshaking, and then it attemps to connect but fails?  Or is the failure before it even gets to the point of handshaking?

Tell me more about how far it gets before it disconnects.

Alan

---

### Post by rboik on 2006-07-15
I get a dial tone and everything, it connects and then kicks off, it has to be because I don't have it setup right.

---

### Post by editrix on 2006-07-15
It's a well-known problem. Try commenting out the line:
auth
in /etc/ppp/options.

---

