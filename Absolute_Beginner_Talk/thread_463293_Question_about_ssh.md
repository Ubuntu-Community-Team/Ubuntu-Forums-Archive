---
title: "Question about ssh"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by boom2k1 on 2007-06-03
I am connected to an ssh server using ssh.
I would like to work with the coding files stored on the server.

How would I be able to work with those text files?
I only know I can use vi. Are there any other options I can do?
(Preferrably I want to use a graphical text editor... how can I do that without actually downloading the file and uploading back the file everytime I want to see my changes? - Thanks)

---

### Post by Ptero-4 on 2007-06-03
you can do ssh -X to conect your X11 to the remote system`s X11 (provided both hosts have X11).

---

### Post by boom2k1 on 2007-06-03
Thanks man. this works just as I wanted. :) I never know ssh is that powerful :)

(now i can use gedit)

Any other suggestions?

---

### Post by hyper_ch on 2007-06-03
well, I use Konqueror and Kate... with Konqueror I can connect to the remote ssh server (= fish://user@server) and then I have assigned .php files with KATE on my computer :)

---

