---
title: "Changing the WWW folder in Ubuntu Server"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Holmes89 on 2008-02-09
I need to access my Ubuntu Server drive somehow in order to change my web page but I do not know how to do this, I currently have it on a thumb drive and I do not have (nor do I want) a gui for Ubuntu Server unless it is really lite. Does anyone know how I can change my folder so I can update my website?

---

### Post by gate on 2008-02-09
define "change your folder" pls?



  There are several ways depending on what you want. If you want to make it so your web server looks for the root of your flash drive instead of /var/www you could alter /etc/apache2/sites-available/default  (or the site configuration file for what you are doing) to point to /media/disk/
I **DO NOT** recommend doing this. The better path is that when you want to update your site, copy the files from your flash drive to /var/www/

   
  or do you mean 'how do I access my flash drive files'?

---

