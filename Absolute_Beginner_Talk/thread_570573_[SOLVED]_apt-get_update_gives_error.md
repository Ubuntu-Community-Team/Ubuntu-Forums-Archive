---
title: "[SOLVED] apt-get update gives error"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by arjayes on 2007-10-08
running apt-get update gives this error

W: GPG error: [http://repository.debuntu.org](http://repository.debuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E466170BCF1FC29
  help please

---

### Post by Dr Small on 2007-10-08
```
wget http://repository.debuntu.org/GPG-Key-chantra.txt -O- | sudo apt-key add - 
```

---

### Post by arjayes on 2007-10-08
thanks . it worked but what  exactly does that command do.:KS

---

### Post by hyper_ch on 2007-10-08
```

man wget

```
```

man apt-key

```
```

man sudo

```

---

### Post by Dr Small on 2007-10-08
I took that command directly from repository.debuntu.org, and it was their suggestion to run that command to solve your problem.

Dr Small

---

### Post by Seisen on 2007-10-08
In a nutshell it downloads the GPG key from their repository and then adds their GPG key to apt-key so that it can verify that the packages you download from that particular repository are authentic.

---

