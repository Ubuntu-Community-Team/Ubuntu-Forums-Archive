---
title: "Can't Install Automatix Behind Proxy Requiring Authentication at Work"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by utnubu_resu on 2006-06-07
At work I am behind a proxy requiring authentication. I used the install directions for Automatix at [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) but always get a 407 Proxy Authentication Error that occurs when I run the first of the two lines below:

wget [http://beerorkid.com/arnieboy/automatix_6.1_i386.deb](http://beerorkid.com/arnieboy/automatix_6.1_i386.deb) 
sudo dpkg -i automatix_6.1_i386.deb 

The link [http://ubuntuforums.org/showpost.php?p=541276&postcount=1006](http://ubuntuforums.org/showpost.php?p=541276&postcount=1006) on Automatix install page deals with proxies but it doesn't address authentication.

I browsed the Ubuntu forums and came across many posts regarding how to edit .wgetrc and apt-get to get through a proxy requiring authentication.  I tried everything mentioned to no avail.  I also did extensive Google searching on Automatix, wget, and apt-get and tried everything I came across, including wget command line options and still no-go.

This is where I am at right now:

1.) Firefox works after entering proxy info in that program.

2.) I can get through the proxy when using Synaptic by entering in this format: 

proxyuser:proxypw@proxy.my.com:port 

3.) I've edited .wgetrc and it now looks like this: 

# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = [http://proxy.myproxy.com:8080/](http://proxy.myproxy.com:8080/)
ftp_proxy = [http://proxy.myproxy.com:8080/](http://proxy.myproxy.com:8080/)
proxy_user = proxyusername 
proxy_passwd = proxypassword 
# If you do not want to use proxy at all, set this to off.
use_proxy = on

I also tried to use http_proxy=proxyuser:proxypw@proxy.my.com:port instead of using the separate proxy_user and proxy_passwd lines but that didn't work, either.

4.) I've tweaked apt-get, too, even watching for the space between proxy and http when doing:

ACQUIRE {
http::proxy "http://proxy.myproxy.com:8080/"
}

I tried also

ACQUIRE {
http::proxy "http://proxyname:proxypw@proxy.myproxy.com:8080/"
}

and that didn't work.  

One post regarding apt-get said to add the domain so I even tried [http://mydomain\proxyuser:proxypw@proxy.my.com:port/](http://mydomain\proxyuser:proxypw@proxy.my.com:port/) since it worked for the poster but that didn't work.  

I am using Breezy. I've already entered system proxy info under the System menu, too, for the system as a whole.

Any more ideas?

---

### Post by manro on 2007-02-03
Same problem here....any suggestions?

Thanks! :)

---

### Post by mincho on 2007-05-02
Same Problem here please some one help us

407 proxy authentication error while updating apt-get

---

