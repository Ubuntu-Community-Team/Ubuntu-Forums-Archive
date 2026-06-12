---
title: "cert8.db of iceweacel is changed... is it hacked?"
date: 2012-03-18
forum: Any Other OS
---

### Post by q.dinar on 2012-03-18
hello
i backed up my system and have discovered that cert8.db of firefox is changed. they said to me in #firefox in freenode, that it can change only by update, or when i accept unknown certificate. i have not accepted unknown certificate nor updated firefox since last backup... i will show packages installed since last backup, (in case one of they may change certificate, but i am sure only mozilla packages "may do so", because it is changed only in one profile, and profile folders has random names):
grep installed /var/log/dpkg.log|grep -v half
...
2012-03-12 12:06:16 status installed man-db 2.5.7-8
2012-03-12 12:06:18 status installed menu 2.1.44
2012-03-12 12:06:19 status installed gnome-menus 2.30.3-1
2012-03-12 12:06:19 status installed desktop-file-utils 0.15-2
2012-03-12 12:06:20 status installed libgc1c2 1:6.8-1.2
2012-03-12 12:06:21 status installed libexiv2-9 0.20-2
2012-03-12 12:06:21 status installed exiv2 0.20-2
2012-03-12 12:06:21 status installed imagemagick 8:6.6.0.4-3+squeeze1
2012-03-12 12:06:21 status installed libgsl0ldbl 1.14+dfsg-1
2012-03-12 12:06:21 status installed libgtkspell0 2.0.16-1
2012-03-12 12:06:22 status installed libmagick++3 8:6.6.0.4-3+squeeze1
2012-03-12 12:06:22 status installed inkscape 0.47.0-2+b1
2012-03-12 12:06:22 status installed libcdt4 2.26.3-5
2012-03-12 12:06:22 status installed libgd2-noxpm 2.0.36~rc1~dfsg-5
2012-03-12 12:06:22 status installed libgraph4 2.26.3-5
2012-03-12 12:06:22 status installed libpathplan4 2.26.3-5
2012-03-12 12:06:22 status installed libxdot4 2.26.3-5
2012-03-12 12:06:22 status installed libgvc5 2.26.3-5
2012-03-12 12:06:22 status installed libmagickcore3-extra 8:6.6.0.4-3+squeeze1
2012-03-12 12:06:23 status installed libnetpbm10 2:10.0-12.2+b1
2012-03-12 12:06:23 status installed libplot2c2 2.5-4
2012-03-12 12:06:23 status installed libpstoedit0c2a 3.50-3+b1
2012-03-12 12:06:23 status installed libwmf-bin 0.2.8.4-6.1+b1
2012-03-12 12:06:23 status installed netpbm 2:10.0-12.2+b1
2012-03-12 12:06:23 status installed perlmagick 8:6.6.0.4-3+squeeze1
2012-03-12 12:06:23 status installed pstoedit 3.50-3+b1
2012-03-12 12:06:23 status installed ufraw-batch 0.16-3+b1
2012-03-12 12:06:25 status installed menu 2.1.44
2012-03-16 16:16:05 status installed man-db 2.5.7-8
2012-03-16 16:16:07 status installed tcpdump 4.1.1-1
i have checked my browsing history, i have not been in site which asked to accept certificates, even if would, i do not accept forever, only a certificate of "webmoney" is accepted forever by me.

i will attach 2 certificates. old is with "1", new is with "2".

yesterday or before it my iceweasel is crashed 2 times while i was watching embedded youtube.

i am using debian squeeze, i could not attach files in mozillazine and debian forums, so i post here. another option is mozilla support forum... but i see there is no attachments.

firefox version is iceweasel 3.5.16

---

### Post by q.dinar on 2012-03-18
( you can compare the 2 cert8.db files with total commander... )

---

### Post by q.dinar on 2012-03-18
i have copied this post to [http://forums.mozillazine.org/viewtopic.php?f=7&t=2445179](http://forums.mozillazine.org/viewtopic.php?f=7&t=2445179)

---

### Post by q.dinar on 2012-03-18
i have copied this post to:

[https://support.mozilla.org/ru/questions/923278](https://support.mozilla.org/ru/questions/923278)

[http://ubuntuforums.org/showthread.php?t=1942838](http://ubuntuforums.org/showthread.php?t=1942838)

---

### Post by q.dinar on 2012-03-18
meaningful changes i retrieved with TC file comparison:
old and new values separated by 1 empty line (there extra new lines appeared in linux):


"Secure Digital Certificate Signing1)0


"Secure Digital Certificat    &#1047; 






UIL10U

StartCom Ltd.1+0)U"Secure Digital Certificate Signing1806U/StartCom Class 1 Primary Intermediate Server CA0


t AB1&0$UAddTrust External TTP Network1"0 UAddTrust External CA Root0
101207000000Z
200530104838Z0Q10	UUS10U





&#8218;"0
	*&#8224;H&#8224;&#1095;
 &#8218; 0&#8218;
&#8218; ¶&#8240;&#1046;¬&#1087;	Rx¬&#8217;c&#1056;&#1092;D&#8222;&#1026;V&#8216;®&#1073;


	Internet210UInCommon10UInCommon Server






0&#8224;[http://ocsp.startssl.com/ca0-+0&#8224;!http://www.startssl.com/sfsca.crt0](http://ocsp.startssl.com/ca0-+0&#8224;!http://www.startssl.com/sfsca.crt0)[UT0R0'*%*#&#8224;![http://www.startssl.com/sfsca.crl0'*%*#&#8224;!http://crl.startssl.com/sfsca.crl0&#1027;&#1026;U](http://www.startssl.com/sfsca.crl0'*%*#&#8224;!http://crl.startssl.com/sfsca.crl0&#1027;&#1026;U) y0w0u+&#1027;µ70f0.+"http://www.startssl.com/policy.pdf04+([http://www.startssl.com/intermediate.pdf0](http://www.startssl.com/intermediate.pdf0)
	*&#8224;H&#8224;&#1095;
 &#8218; !	I>&#1168;&#8364;

]0U&#1103;0U&#1103;0&#1103; 0U 

00U  0DU=0;09*7*5&#8224;3http://crl.usertrust.com/AddTrustExternalCARoot.crl0&#1027;&#1110;+&#1027;¦0&#1027;&#1032;0?+0&#8224;3http://crt.usertrust.com/AddTrustExternalCARoot.p7c09+0&#8224;-http://crt.usertrust.com/AddTrustUTNSGCCA.crt0%+0&#8224;[http://ocsp.usertrust.com0](http://ocsp.usertrust.com0)
	*&#8224;H&#8224;&#1095;
 &#8218; 






&#1075;&#1083;&#1065;&#1112;&#8221;®j&#1075;bb&#8211;&#1025;d|&#1105;&#8225;&#1091;&#8482;2~&#8217;&#1118;R&#1109;»&#1096;e&#1055;&#1049;&#1090;0


&#1074;h&#1043;pf_&#1059;InCommon Server CA q&#1041;&#1059;





QZieCIq&#1045;&#1072;o&#8221;4k&#1094;&#1064;©°L~S&#1083;&#1039;H&#1071;&#1050;3µH&#1098;6JS¦3&#1056;&#8240;&#1053;I&#1053;&#8240;1<&#1106;&#1040;r&#1063;eKR5&#1033;FD&#8470;=&#1035;(e¦>y&#1115;\D)*°5.!N&#1105;&#1058;&#1079;>]&#8222;&#1107;&#1110;&#1043;&#1042;&#1076;&#1058; 

U

AddTrust AB1&0$UAddTrust External TTP Network1"0 UAddTrust External CA Root 





&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103; 


     InCommon Server CA  &#1027;  q&#1041;&#1059;&#1118;&°&#1058;±&#1091;&#1078;&#1027;gd>0o10	USE10U
AddTrust AB1&0$UAddTrust External TTP Network1"0 UAddTrust External CA Root0Q10	UUS10U
	Internet210UInCommon10UInCommon Server CA 






&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103;&#1103; 


&#1103;  S0Q10	UUS10U
	Internet210UInCommon10UInCommon Server CAInCommon Server CA

---

### Post by q.dinar on 2012-04-17
have copied to [http://forums.debian.net/viewtopic.php?f=6&t=78484](http://forums.debian.net/viewtopic.php?f=6&t=78484)

---

