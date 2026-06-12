---
title: "Configure: error: OpenSSL"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2007-03-19
I have OpenSSL installed and I am trying to configure TOR, when i run the command ./configure && make everything installs and at the end i get this error any ideas?

checking for OpenSSL directory... configure: error: Could not find a linkable OpenSSL. You can specify an explicit path using --with-ssl-dir

Thanks

---

### Post by Bachstelze on 2007-03-19
```
sudo apt-get install libssl-dev
```

---

### Post by poordamnedfool on 2007-03-19
Thanks that worked

---

