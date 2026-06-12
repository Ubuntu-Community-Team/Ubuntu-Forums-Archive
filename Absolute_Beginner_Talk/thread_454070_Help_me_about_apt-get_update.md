---
title: "Help me about apt-get update"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by mrKaqz on 2007-05-25
I tyird to update by command "sudo apt-get update".

And the end of resault show 


```


Reading package lists... Done
W: GPG error: http://ubuntu.beryl-project.org feisty Release: The following signatures were invalid: BADSIG 3FF0DB166A7476EA Nicholas Thomas (Repository signing key) <root@lupine.me.uk>
W: You may want to run apt-get update to correct these problems

```

how can I fix it?

---

### Post by Smu on 2007-05-25
You need the GPG-key...

Run this line in terminal:

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

---

### Post by mrKaqz on 2007-05-25
> **Smu said:**
> You need the GPG-key...

Run this line in terminal:

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

I do it but it's doesn't help.
When I run update I got same problem.

---

### Post by Smu on 2007-05-25
Weird... It should do it. Try checking if other people hava had problems with the beryl repositories GPG key... 

Here's the repository page. Try copy pasting the line from there...  [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/)

---

### Post by mrKaqz on 2007-05-26
I tried to restart my computer and do it again.
It's work.

Thank you man.

---

### Post by taurus on 2007-05-26
It guess it works on your machine now.

---

