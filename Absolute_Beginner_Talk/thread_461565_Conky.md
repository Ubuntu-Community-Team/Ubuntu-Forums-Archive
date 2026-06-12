---
title: "Conky"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by khardbored on 2007-06-01
I'm able to edit conkyrc files just fine. It's actually not all that greek to me right now, sweet. My problem is, how can I load multiple rc files? Im trying out a demo and it needs to load up three scripts. I am able to load one just fine via conky -c path/to/script but I need to load two more, how would I do that view command line? Thanks guru guys!

---

### Post by freakavoid on 2007-06-01
As far as I know you cannot load more than one config file pro instance. You can let the conky executable run more than once however. Doesn't this work for you? I mean like

```

conky -c /path/to/config/1
conky -c /path/to/config/2
conky -c /path/to/config/3

```

---

### Post by khardbored on 2007-06-01
I guess since I was doing this via a terminal window and the deamon, once run, was stuck inside the console that I was bothered. But alas, I can just run conky with the -d switch to hide the daemon, sweet.

Thanks. I think your code would work if I just dropped it in a file and +x'd it?

---

### Post by freakavoid on 2007-06-01
Sure it would. You can also send the process directly to the background by using '&'. e.g.

```

conky -c /path/to/config/x&

```

Another useful tip is ctrl+z. You can use ctrl+z key combination in a terminal to send any process in the background. It will stop and you can make it continue by typing 'bg'. And 'fg' will put it again in the foreground.

---

