---
title: "Firefox - security protocol not enabled"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by richardward101 on 2007-01-27
I'm trying to access my university Portal at [http://my.nottingham.ac.uk](http://my.nottingham.ac.uk) and firefox says:

Firefox cannot connect securely to (above site) because the site uses a security protocol that isn't enabled.

Needless to say I eed to use the site often, and using IE in wine is becoming a drag. Any ideas on what I can do to enable the security protocol?
Thanks

---

### Post by yi0dj5yaobibfpx@put2.net on 2007-02-04
Here is how I resolved this issue:

1. In firefox type in about:config in the url field.
2. There is a key called security.enable_ssl2 toggle it to true.

Thats it!! Go to your website and enjoy.

PS: I'm not a registered user, and the email is fake, so you dont have to reply to thank me:)

---

### Post by yi0dj5yaobibfpx@put2.net on 2007-02-04
I'm sorry, for your website I needed to set the following to true.

security.ssl3.rsa_rc4_40_md5  

This would do the trick. I just tested it. have fun!!!

---

### Post by richardward101 on 2007-02-09
thanks, I actually enabled ALL the security protocols, but now I know which it is I can disable the rest. Much obliged.

---

### Post by koti123 on 2007-10-29
Hey ppl I have tried both of this turning it true but still am getting this mesage  "Firefox can,t connect securely to (ssl enabled site:) because the site uses a security protocol which isn't enabled "and am not able access the web sites which are ssl enabled, can you please help. 

 1. security.ssl3.rsa_rc4_40_md5 = True
 2. security.enable_ssl2 = True

 F1, F1, F1 ...!!!

koti

---

### Post by dsplabs on 2008-01-05
I had the same problem on our university portal: [https://www69.gu.edu.au:8443/selfcare.php]("https://www69.gu.edu.au:8443/selfcare.php") and enabling security.ssl3.rsa_rc4_40_md5 was what worked for me too. But you may have to try enabling other protocols. Here is a detailed walk through: [http://linux.dsplabs.com.au/?p=59]("http://linux.dsplabs.com.au/firefox-config-cant-connect-securely-security-protocol-not-enabled-p59/").

---

