---
title: "What happened to phpmyadmin?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by JengaBlocks on 2007-07-18
I did a search with Synaptic Package manager and it doesn't even show up. Is it installed with another package? If not, why isn't it made available in the repositories? Its one of the most popular mysql/php packages out there!

---

### Post by tarek on 2007-07-18
phpmyadmin is available in the universe repository. Go to System > Administration > Software Sources and enable the repository.

Open up a terminal and enter this command to install it:
```

sudo aptitude update
sudo aptitude install phpmyadmin
```

By default, it should create a shortcut under /var/www/ but if not run this command:
```
sudo ln -s /usr/share/phpmyadmin/ /var/www/
```

If you're looking for a software but don't know what repository check this page: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

Select your version and find the package.

Tarek

---

### Post by JengaBlocks on 2007-07-18
Thank you Tarek ... I just re-installed Ubuntu again and forgot about the repository settings.

Yes, phpmyadmin is primarily stored in the /var/www directory which is perfectly fine as it is in the document root for Apache2.

---

