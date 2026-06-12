---
title: "another problem , couldn't read character during installation."
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by feelexit on 2006-07-22
I just installed links on my server.

[IMG]http://www.qjcreative.com/bug.jpg[/IMG]

those characters are not readable.  during the installation of the ubuntu server, I pick chinese as language. probably those unreadable characters are chinese.

how can i fix it or switch it back to english. thank you.

---

### Post by abowman on 2006-07-22
Try installing language-pack-en through synaptic or:
```

sudo apt-get install language-pack-en

```

You might have to uninstall language-pack-zh
```

sudo apt-get remove language-pack-zh

```

---

