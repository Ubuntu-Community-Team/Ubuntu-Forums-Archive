---
title: "Linksys PCM100 card with Dapper"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by ChasP505 on 2007-03-25
A friend installed Ubuntu Dapper on my old Dell Inspiron 7000 (formerly ran Windows 98). Now it doesn't recognize my Linksys PCM100 Fast Ethernet 10/100 card. We have searched unsuccessfully for drivers for this card. Any help?

---

### Post by stanner on 2007-03-26
You might want to try opening terminal and issuing the following command dmesg | grep eth, and also lsmod, post the results and let us know what you find.  Also is your card version 1 or version 2?  You should be able to figure this out by using the cardctl command.

---

### Post by ChasP505 on 2007-03-26
Wow! Whatever that command was, it worked. I now have a connection. Also, it seems that this install is not Dapper, but Edgie 6.10. Thanks. I have a lot to learn.

Now I have to work on my Linksys wireless G card.

---

### Post by user2037 on 2007-09-11
Same issue on Dapper here though there is no "cardctl" command. Only "pccardctl" and it reports:
```

Socket 1:
  5.0V 16-bit PC Card

```

"dmesg | grep eth" comes up empty

"dmesg | grep PCM"
```

[...] pccard: PCMCIA card inserted into slot 1

```

"lsmod | grep pcmc"
```

pcmcia      40508  0
pcmcia_core 42640  3 pcmcia,yenta_socket,rsrc_nonstatic

```

---

