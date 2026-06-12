---
title: "CITRIX for ubuntu 7.04"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by mr2v6 on 2007-09-19
Greetings, 
Is there a way to install Citrix to Ubuntu.  I followed a link called planetmy (planet malaysia blog) and it still won't work.  

Any help would be appreciated. 

thank you,
Raymond

---

### Post by justleen on 2007-09-19
yes, there is.. 
ive installed it succesfully on both Fedora Core 7 and on Unbuntu Feisty.

from my work documentation (this is for fedora, so you'll have to find these RPM files as .deb files, and unpack the openmotif one)



needed packages are:
ICAClient-10.6-1.i386.rpm
openmotif-2.3.0-0.1.9.3.i386.rpm




first, you need to install OpenMotif 2.2 
the ICA client needs some lib file, which are provided by the RPM packages. Dont install the package just unpack! 


(in /tmp for example)
# rpm2cpio openmotif-2.3.0-0.1.9.3.i386.rpm | cpio -ivd

copy the libs:
# cp ./usr/lib/libXm.so.4.0.0 /usr/lib

create the needed symlinks symlinks:
# cd /usr/lib

# ln -s libXm.so.4.0.0 libXm.so.4

# ln -s libXm.so.4.0.0 libXm.so.3


install the  ICA rpm, with out deps!!! 
# rpm -ivh ICAClient-10.6-1.i386.rpm --nodeps


you can now lauch the ica mangager, or start the saved ica file
/usr/lib/ICAClient/wfcmgr/
/usr/lib/ICAClient/wfica /home/[user]/launch.ica

---

### Post by auditar on 2007-09-19
Here's another set of instructions for Feisty

[COLOR="Blue"]**[http://www.planetmy.com/blog/?p=332]("http://www.planetmy.com/blog/?p=332")**[/COLOR]

---

### Post by justleen on 2007-09-19
> **auditar said:**
> Here's another set of instructions for Feisty

[COLOR="Blue"]**[http://www.planetmy.com/blog/?p=332]("http://www.planetmy.com/blog/?p=332")**[/COLOR]

ohw, you mean the one he already tried???

---

### Post by tenjin1 on 2007-09-19
How to Install Citrix ICAClient 10

    * Install Open Motif (>=2.2): 

```
sudo apt-get install motif-clients
```

    * Get and install Citrix ICA Client (English package) 

```
wget -c http://download2.citrix.com/en.linuxx86.tar.gz
```

or

```
wget -c http://download2.citrix.com/files/en/products/client/ica/current/linuxx86.tar.gz
```

If wget doesn't work, then go directly to the website and download the package -> [http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323#top]("http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323#top")
   
 * Unpack and install (use the proper version downloaded): 

```
gunzip en.linuxx86.tar.gz
tar xvfz en.linuxx86.tar
./setupwfc

```

    * Enable certificate verification in Firefox: 

```
Applications-->Firefox Web Browser-->Advanced-->Encryption-->View Certificates-->Authorities
```

    * Find your certificate authority and click on it. 

```
 Edit-->"This certificate can identify web sites."
```


    * Make sure your Firewall (IPTables) are set to allow Citrix ports (1494, sometimes 443 and 1603). 

How to Uninstall Citrix ICAClient 10

```
/usr/lib/ICAClient/setupwfc
```

---

### Post by auditar on 2007-09-19
> **justleen said:**
> ohw, you mean the one he already tried???

oops...I must start paying better attention:oops:

---

### Post by mr2v6 on 2007-09-22
Hello,
Thank you for the replies.
I have gotten this far.  Citrix is installed, however I am getting this message.

You have not chosen to trust equifax secure global, the issuer of the server security certificate {SSL error 61}

I have done the certificates, I think the problem is the IPtable, and firewall.  How do I get there to configure it the right one?
thanks,
Raymond

---

### Post by tenjin1 on 2007-09-23
> **mr2v6 said:**
> Hello,
Thank you for the replies.
I have gotten this far.  Citrix is installed, however I am getting this message.

You have not chosen to trust equifax secure global, the issuer of the server security certificate {SSL error 61}

I have done the certificates, I think the problem is the IPtable, and firewall.  How do I get there to configure it the right one?
thanks,
Raymond

Looks like you are using Equifax to secure the certificates from your error above.

So not sure about them but you can use the certificate part in Firefox I posted above by...Thawte Consulting cc-->Thawte Serve CA as the authority to identify web sites.
Download the certificates from [http://www.thawte.com/roots/]("http://www.thawte.com/roots/") unzipped the file, find the certificate needed, and copy it (changing the extension slightly) to the  ICAClient certificate folder:

```
cp ThawteServerCA.cer ~/ICAClient/keystores/cacert/ThawteServerCA.crt 
```

---

### Post by mr2v6 on 2007-09-26
Hi,
Now, this is the problem I am currently getting.  How do I adjust this?
Thanks,
Raymond

-------
Client error:
Proxy connection failed: ProxyHost parameter required for custom proxy configurations.

---

### Post by freyes on 2007-09-29
> **tenjin1 said:**
> Looks like you are using Equifax to secure the certificates from your error above.

So not sure about them but you can use the certificate part in Firefox I posted above by...Thawte Consulting cc-->Thawte Serve CA as the authority to identify web sites.
Download the certificates from [http://www.thawte.com/roots/]("http://www.thawte.com/roots/") unzipped the file, find the certificate needed, and copy it (changing the extension slightly) to the  ICAClient certificate folder:

```
cp ThawteServerCA.cer ~/ICAClient/keystores/cacert/ThawteServerCA.crt 
```
Thx dude, this saved my life. with this tip  I made it work the citrix client. :)

---

### Post by tenjin1 on 2007-10-01
> **mr2v6 said:**
> Hi,
Now, this is the problem I am currently getting.  How do I adjust this?
Thanks,
Raymond

-------
Client error:
Proxy connection failed: ProxyHost parameter required for custom proxy configurations.

Hi

Not too sure about that error, but sounds like you are using a proxy? Are you using any firefox add-ons for proxy? If so, try disabling that. Also make sure your citrix client isnt setup to use proxy. Like I said I'm not too sure what is going on...but check all your settings for proxy and make sure you aren't using them.

---

### Post by ericsp on 2007-10-10
I had everything up and running, until our institute changed the certificate. I downloaded the new certificate and put it into the correct directory. This did not fix the "You have decided not to trust..." Any suggestion?

Eric :confused:

---

### Post by P|iET&gt; on 2007-10-18
Hi dear

I got also a problem with running icaclient on my ubuntu. I don't know if this is the good place to ask my question (the problem above isn't solved yet). When I try to use icaclient, the screen of the application is black. First a screen with "Citrix Metaframe" appears, folowed by two black screens. I installed citrix several times and the problem keeps appearing. Is there anyone who knows what went wrong? I can't even guess...

Thanks a lot

---

### Post by Padre on 2007-10-19
> **ericsp said:**
> I had everything up and running, until our institute changed the certificate. I downloaded the new certificate and put it into the correct directory. This did not fix the "You have decided not to trust..." Any suggestion?

Eric :confused:

May be different encryption method use?

---

### Post by ericsp on 2007-11-01
How do I find out if the decryption method has changed?

Eric

---

### Post by jlchannel on 2007-11-08
Upgrade to Ubuntu 7.10. 

Another useful link from Planet Malaysia Blog.  
[http://www.planetmy.com/blog/how-to-install-citrix-icaclient-on-ubuntu-710-gutsy-gibbon/](http://www.planetmy.com/blog/how-to-install-citrix-icaclient-on-ubuntu-710-gutsy-gibbon/)

---

### Post by wscheer on 2007-12-04
ubuntu 7.10
citrix - latest version

I was having a problem after my company got a new citrix ssl where I was getting the "equifax business ca-1 blah blah blah (ssl error 61)"

to fix it I had to download the trusted cert from [http://www.geotrust.com/resources/root_certificates/index.asp](http://www.geotrust.com/resources/root_certificates/index.asp)

then copy it (as root) into usr/lib/icaclient/keystore/cert folder. After that it seems to be working ok now.

hope that helps someone.

---

### Post by Abelius on 2008-04-30
Moving and renaming the certificate file to /usr/lib/ICA....... worked for me, but make sure you chmod it to allow read permission as well.

---

### Post by ben.maritz on 2008-05-28
Hi! I'm having this same problem, except with the following error:

"You have not chosen to trust "AAA Certificate Services", the issuer of the server's security cerrificate (SSL Error 61)."

I have found the certificate in the /usr/share/ca-certificates/mozilla/ directory and copied it into the /usr/lib/ICAClient/keystore/cacerts/ folder, but this didn't work! Still get the same error! Any ideas?

By the way, I am running Ubuntu 8.04 now...

Thanks!


Ben

---

### Post by ThonyJ on 2008-06-18
Hi Ben

Here is the solution that worked for me in both ubuntu 7.04 and 8.04:
I downloded the certificate from Comodo at [https://support.comodo.com/index.php?_m=downloads&_a=viewdownload&downloaditemid=56&nav=0,1](https://support.comodo.com/index.php?_m=downloads&_a=viewdownload&downloaditemid=56&nav=0,1) 

/ Thony

---

