---
title: "Permanent proxy in Terminal"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-17
How to permanently give proxy in terminal?

Adding
```

http_proxy="http://Username:Userpwd@server:ServerPort/
export http_proxy

```
to
/etc/environment???
/root/.bashrc???

or adding:
```

Acquire::http::proxy
{
export http_proxy="http://Username:Userpwd@server:ServerPort/"
};

```
to

/etc/apt/apt.conf

PS:
I asked the same question in another thread, but i wasn't clear so created an other thread specifically for it.

---

### Post by shoaibi on 2007-02-18
Hmmm got it,
its in /etc/environment
Thanks anways, afterall there were 13 views ;) 
waiting for response on pyWings Installation Thread.

---

### Post by bapoumba on 2007-02-18
Hello,
Nice to see you got it to work. Did not know what to suggest in addition to what I had already posted in your other thread ;)

---

### Post by shoaibi on 2007-02-18
Hmmm thanks bapoumba, well i did some logix work here ;), i tried /etc/enviornment first, and it worked, thus my logix was good, Voilla i just mastered Ubuntu terminal proxy settings ;) ;) :D
hmmm can you check the other threadabout pyWings installation?

---

### Post by bapoumba on 2007-02-18
Sorry, I had a look already ...

---

