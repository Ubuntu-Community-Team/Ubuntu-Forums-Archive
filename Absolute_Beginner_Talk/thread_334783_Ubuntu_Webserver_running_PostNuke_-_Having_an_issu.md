---
title: "Ubuntu Webserver running PostNuke - Having an issue"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by ShawnHunt on 2007-01-09
Hey everyone, I don't really know where else to post this.  I've tried all of the other sites related to my question, but nobody can seem to help me.  I'm putting it out to the ubuntu community to help me solve my problem!  ;)

I have a ubuntu server setup as a web server running apache2 with php5, setup with ISPconfig.  On this machine, I am running a domain using PostNuke as the cms.  A module I am using, Mediashare, is causing me some problems and I think it has to do with the ownership of files, though that's just a guess.  Someone else suggested checking the GID/UID, but I haven't been able to find any relevant info on the subject.

Here is the error that I am getting.

    *  /var/www/web1/web/modules/mediashare/pnvfs_fsdirectapi.php(44): Failed to copy file '/var/www/web1/web/tmp/Preview1CMK5f' to '/var/www/web1/web/mediashare/5h/61kvlo3xz4ainhcdbjocdg4r74i4a2-tmb.png' while creating new file in virtual storage system. Please check media upload directory in admin settings and it's permissions.

---

### Post by az on 2007-01-09
Any directory that your CMS is trying to wrtite to would need to be owned by www-data (or at least be writeable by everyone).

---

### Post by ShawnHunt on 2007-01-09
How do I tell who the owner of the file / directory are?  I am sshing in through cyberduck and it says "0" for owner and group.  Is this correct?  Thanks for your help, it's appreciated.  :)

---

### Post by cloakable on 2007-03-20
That's odd. I know "1" is the root id for both user and group, but "0", I have no idea. Try

chown -R www-data:www-data /var/www/web1/web/mediashare/

And see if that helps.

---

### Post by lingnoi on 2007-03-20
You can tell who owns what and the file permissions by typing
 ```
ls -l
```

---

