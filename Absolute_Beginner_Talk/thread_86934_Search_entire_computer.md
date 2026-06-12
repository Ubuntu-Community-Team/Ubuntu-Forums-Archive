---
title: "Search entire computer"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by HokeyFry on 2005-11-06
how do you search the entire computer and not just one single directory?

---

### Post by adwait on 2005-11-06
There is a search tool in the "Places menu right? There you can choose to search the entire file system if I am not mistaken.

---

### Post by poptones on 2005-11-06
Run "sudo locate -u" to get things started with slocate. When it's finished indexing your drives it will be ready to searchand you can look for filenames by typing "locate (whatever)"

type "man locate" for instructions on using it. The "Find" on yur ubuntu menu will also allow you to search by file contents, but the panel "find' tool is much, much slower because of this.

---

### Post by HokeyFry on 2005-11-06
thanks poptones. searching works much better now that the drive is indexed.

---

### Post by kvidell on 2005-11-06
is sudo updatedb the same as sudo locate -u?
- K

---

### Post by Lambert on 2005-11-06
> is sudo updatedb the same as sudo locate -u?

yes

---

