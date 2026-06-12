---
title: "bluetooth discovery"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by docetes on 2007-03-11
how do i make my laptop "discoverable" when using bluetooth?

---

### Post by Delvien on 2007-03-11
Have bluetooth on. :) its automatically discoverable.

---

### Post by docetes on 2007-03-11
and how would i find my ip address so i can get my chat client can connect to my chat server on my laptop? I'm using TCP/IP for communication

---

### Post by Delvien on 2007-03-11
If you know the bdaddr of the device you are trying to connect to then use the following command to connect just with bluetooth:

```
sudo hidd --connect 00:AA:00:BB:00
```

If you are looking for this to be your network, im not sure how to do it

---

### Post by docetes on 2007-03-11
how do i find my laptops bdaddr?

---

