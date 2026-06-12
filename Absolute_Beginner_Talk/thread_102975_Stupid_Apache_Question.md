---
title: "Stupid Apache Question"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by Vaerok on 2005-12-13
I'm fairly sure this is just because it's midnight but I have a really stupid question. I've installed apache2, php5 and MySQL and they all work. My question is, how do i upload to my website? The /var/www/ folder has no write permissions. Should I do a "sudo chmod 775 /var/www/" or something? Or is there, as i suspect, a much simpler option? I only intend to access the server locally if that helps.

---

### Post by lutrafobic on 2005-12-13
I think the best way is to set your username as the owner of the /var/www folder.
```
cd /var
sudo chown -R yourusername www
```

That would mean that you are the owner, not root, which means yourusername should have access to change stuff inside it. If it stil isn't giving you permissions, even tho your the owner, you could try:
```
cd /var/www
sudo chmod 744 *
```

---

### Post by Vaerok on 2005-12-13
Thanks for that, I had to use 755 in the end though. I assume thats because I was using php.

EDIT: How do I set it so that every new file I create automatically has 755 permissions?

---

