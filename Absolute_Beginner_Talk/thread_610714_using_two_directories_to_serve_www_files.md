---
title: "using two directories to serve www files"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by HurricaneDan on 2007-11-12
I am looking to add another server to serve webpages but actually have files on both machines that will continue to be served.

For example, I am currently serving files on [www.example.com](www.example.com) and my new server is set up as newwww.example.com.  I am sure that I will need to change the httpd.config file from pointing to the www server to the newwww server.

Here is where the confusion comes in for me.  I also have two subdirectories on the www server (clients and customers).  They are a not subdomains but are [www.example.com/clients](www.example.com/clients) and [www.example.com/customers](www.example.com/customers).  Their directories are in the www/htdocs/clients and www/htdocs/customers directories respectively.

What I need to have happen is when someone goes to [www.example.com](www.example.com) it actually points to the www/htdocs directory on newwww but if someone types in [www.example.com/clients](www.example.com/clients) it displays the files from www, not trying to find a directory www/htdocs/clients on the newwww server.

Is this possible?

Thanks,

Dan

---

### Post by constrictor on 2007-11-12
I would put in an index.html file that redirects to where you want them to go.

---

### Post by skillet on 2007-11-12
I would just use a NFS mount

---

### Post by HurricaneDan on 2007-11-12
So you are saying to not use the httpd.conf at all?

Just do a redirect on the new server using a duplicate directory (say, community/index.html) that points back to the old server?

I am not sure how the redirect would look and I may have not made something clear -  when the new site (currently newwww, for testing) goes live it will be reached by typing [www.example.com](www.example.com).  So when someone typed in [www.example.com/community](www.example.com/community) (actual file path //newwww/srv/www/htdocs/community) it would look at the index.html file in that directory and would try to look for the old server but it needs to point to the old server (actualy file path //www/srv/www/htdocs/community).

I hope that cleared it up a little,

Dan

---

