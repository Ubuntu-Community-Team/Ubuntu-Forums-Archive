---
title: "gnome-netstatus-applet, leaving unconfigured headaches"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by wrongboy on 2006-11-17
Hi all. First post. Just upgraded via the official way from Dapper to Edgy, and had two errors during install: one about dependencies, and another one about 'gnome-netstatus-applet'. The upgrade went through fine, though, despite the errors.

Afterwards, I also installed Xubuntu: no errors. As I was in the process of installing Automatix2, I saw issues again regarding dependencies, and besides the previously mentioned applets, these:

ubuntu-desktop
xubuntu-desktop
system-config-printer

All files listed above can be reinstalled from synaptic, but my headache with gnome-netstatus-applet continues.

I did my research, tried updates, dselect's, dpkg's, fiddling around with synaptic, I still get errors, and cannot seem to successfully install related packages. The error usually comes in this form (I was now just removing the applet via terminal [apt-get remove]):

> Removing gnome-netstatus-applet ...
/usr/share/gconf/schemas/netstatus.schemas:271: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0xEB 0x6F 0x20 0x64
        <long>Giao di&#7879;n m&#7841;ng &#273;&#432;&#7907;c theo dõi b&#7903;i B)&#65533;&#65533;&#65533;o d&#65533;e>
                                                              ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 18
&#65533;&#65533;&#3589;ba&#65533;~&#65533;Giao di&#7879;n m&#65533;     &#65533;)&#65533;&#65533;o m&#65533;&#1090;/sh)&#65533;i bGia:&#1088;&#65533; <l&#65533;&#65533;&#65533;e>&#65533;a&#65533;&#65533;b the&#7841;
          ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : error parsing attribute name
&#65533;&#65533;&#3589;ba&#65533;~&#65533;Giao di&#7879;n m&#65533;     &#65533;)&#65533;&#65533;o m&#65533;&#1090;/sh)&#65533;i bGia:&#1088;&#65533; <l&#65533;&#65533;&#65533;e>&#65533;a&#65533;&#65533;b the&#7841;
                                                          ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : attributes construct error
&#65533;&#65533;&#3589;ba&#65533;~&#65533;Giao di&#7879;n m&#65533;     &#65533;)&#65533;&#65533;o m&#65533;&#1090;/sh)&#65533;i bGia:&#1088;&#65533; <l&#65533;&#65533;&#65533;e>&#65533;a&#65533;&#65533;b the&#7841;
                                                          ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : Couldn't find end of Start Tag l line 273
&#65533;&#65533;&#3589;ba&#65533;~&#65533;Giao di&#7879;n m&#65533;     &#65533;)&#65533;&#65533;o m&#65533;&#1090;/sh)&#65533;i bGia:&#1088;&#65533; <l&#65533;&#65533;&#65533;e>&#65533;a&#65533;&#65533;b the&#7841;
                                                          ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 23
&#65533;&#65533;&#3589;ba&#65533;~&#65533;Giao di&#7879;n m&#65533;     &#65533;)&#65533;&#65533;o m&#65533;&#1090;/sh)&#65533;i bGia:&#1088;&#65533; <l&#65533;&#65533;&#65533;e>&#65533;a&#65533;&#65533;b the&#7841;
                                                                 ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 3
&#65533;&#65533;&#3589;ba&#65533;~&#65533;Giao di&#7879;n m&#65533;     &#65533;)&#65533;&#65533;o m&#65533;&#1090;/sh)&#65533;i bGia:&#1088;&#65533; <l&#65533;&#65533;&#65533;e>&#65533;a&#65533;&#65533;b the&#7841;
                                                                   ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 23
&#65533;n m&#65533;     &#65533;)&#65533;&#65533;o m&#65533;&#1090;/sh)&#65533;i bGia:&#1088;&#65533; <l&#65533;&#65533;&#65533;e>&#65533;a&#65533;&#65533;b the&#7841;&#65533;o sdõ)&#65533;ao &#65533;e&#65533;&#1087;&#65533;ea
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 3
 m&#65533;     &#65533;)&#65533;&#65533;o m&#65533;&#1090;/sh)&#65533;i bGia:&#1088;&#65533; <l&#65533;&#65533;&#65533;e>&#65533;a&#65533;&#65533;b the&#7841;&#65533;o sdõ)&#65533;ao &#65533;e&#65533;&#1087;&#65533;ea
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 3
&#65533;)&#65533;&#65533;o m&#65533;&#1090;/sh)&#65533;i bGia:&#1088;&#65533; <l&#65533;&#65533;&#65533;e>&#65533;a&#65533;&#65533;b the&#7841;&#65533;o sdõ)&#65533;ao &#65533;e&#65533;&#1087;&#65533;ea&#65533;&#65533;b 
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 18
dõ)&#65533;ao &#65533;e&#65533;&#1087;&#65533;ea&#65533;&#65533;b &#65533;&#65533;b the&#7869;ng>&#432;&#65533; &#65533;eõ)&#65533;ao &#65533;e&#65533;u)&#65533;ib di&#65533;&#65533;Moniy&#65533;aob tg
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 3
&#65533;&#65533;b &#65533;&#65533;b the&#7869;ng>&#432;&#65533; &#65533;eõ)&#65533;ao &#65533;e&#65533;u)&#65533;ib di&#65533;&#65533;Moniy&#65533;aob tgGi&#65533;8&#65533;&#65533;e>&#432;&#65533;  b 
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 3
&#65533;&#65533;b the&#7869;ng>&#432;&#65533; &#65533;eõ)&#65533;ao &#65533;e&#65533;u)&#65533;ib di&#65533;&#65533;Moniy&#65533;aob tgGi&#65533;8&#65533;&#65533;e>&#432;&#65533;  b &#65533;&#65533;b 
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : error parsing attribute name
&#65533;&#65533;ng>&#432;&#65533; &#65533;eõ)&#65533;ao &#65533;e&#65533;u)&#65533;ib di&#65533;&#65533;Moniy&#65533;aob tgGi&#65533;8&#65533;&#65533;e>&#432;&#65533;  b &#65533;&#65533;b &#65533;&#65533; <long-
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : attributes construct error
&#65533;&#65533;ng>&#432;&#65533; &#65533;eõ)&#65533;ao &#65533;e&#65533;u)&#65533;ib di&#65533;&#65533;Moniy&#65533;aob tgGi&#65533;8&#65533;&#65533;e>&#432;&#65533;  b &#65533;&#65533;b &#65533;&#65533; <long-
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : Couldn't find end of Start Tag long- line 273
&#65533;&#65533;ng>&#432;&#65533; &#65533;eõ)&#65533;ao &#65533;e&#65533;u)&#65533;ib di&#65533;&#65533;Moniy&#65533;aob tgGi&#65533;8&#65533;&#65533;e>&#432;&#65533;  b &#65533;&#65533;b &#65533;&#65533; <long-
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 1
&#65533;eõ)&#65533;ao &#65533;e&#65533;u)&#65533;ib di&#65533;&#65533;Moniy&#65533;aob tgGi&#65533;8&#65533;&#65533;e>&#432;&#65533;  b &#65533;&#65533;b &#65533;&#65533; <long-)&#65533; sdb &#65533;D
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 3
 &#65533;e&#65533;u)&#65533;ib di&#65533;&#65533;Moniy&#65533;aob tgGi&#65533;8&#65533;&#65533;e>&#432;&#65533;  b &#65533;&#65533;b &#65533;&#65533; <long-)&#65533; sdb &#65533;D&#65533;&#65533;the 
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 1
&#65533;&#65533;e>&#432;&#65533;  b &#65533;&#65533;b &#65533;&#65533; <long-)&#65533; sdb &#65533;D&#65533;&#65533;the &#65533;d&#65533;ib)figyelt hàzb/localYGi&#65533;&#65533;D
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 3
&#65533;b &#65533;&#65533; <long-)&#65533; sdb &#65533;D&#65533;&#65533;the &#65533;d&#65533;ib)figyelt hàzb/localYGi&#65533;&#65533;D&#65533;&#65533;&#65533;&#65533;the &#65533;)
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 7
&#65533; <long-)&#65533; sdb &#65533;D&#65533;&#65533;the &#65533;d&#65533;ib)figyelt hàzb/localYGi&#65533;&#65533;D&#65533;&#65533;&#65533;&#65533;the &#65533;)&#65533;ad&#65533;g&#65533;,&#65533;
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 3
long-)&#65533; sdb &#65533;D&#65533;&#65533;the &#65533;d&#65533;ib)figyelt hàzb/localYGi&#65533;&#65533;D&#65533;&#65533;&#65533;&#65533;the &#65533;)&#65533;ad&#65533;g&#65533;,&#65533;&#65533;ao&#65533;:
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 3
&#65533;the &#65533;d&#65533;ib)figyelt hàzb/localYGi&#65533;&#65533;D&#65533;&#65533;&#65533;&#65533;the &#65533;)&#65533;ad&#65533;g&#65533;,&#65533;&#65533;ao&#65533;:&#65533;&#37084;&#65533;ib d&#1800;8&#65533;)
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 3
t hàzb/localYGi&#65533;&#65533;D&#65533;&#65533;&#65533;&#65533;the &#65533;)&#65533;ad&#65533;g&#65533;,&#65533;&#65533;ao&#65533;:&#65533;&#37084;&#65533;ib d&#1800;8&#65533;)&#65533;&#65533;d&#65533; &#65533;B&#65533;db &#65533;&#65533;ao&#65533;: 
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 3
àzb/localYGi&#65533;&#65533;D&#65533;&#65533;&#65533;&#65533;the &#65533;)&#65533;ad&#65533;g&#65533;,&#65533;&#65533;ao&#65533;:&#65533;&#37084;&#65533;ib d&#1800;8&#65533;)&#65533;&#65533;d&#65533; &#65533;B&#65533;db &#65533;&#65533;ao&#65533;: &#65533; 
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 7
b/localYGi&#65533;&#65533;D&#65533;&#65533;&#65533;&#65533;the &#65533;)&#65533;ad&#65533;g&#65533;,&#65533;&#65533;ao&#65533;:&#65533;&#37084;&#65533;ib d&#1800;8&#65533;)&#65533;&#65533;d&#65533; &#65533;B&#65533;db &#65533;&#65533;ao&#65533;: &#65533; &#65533;,&#65533;
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : PCDATA invalid Char value 3
&#65533;&#65533;&#65533;&#65533;the &#65533;)&#65533;ad&#65533;g&#65533;,&#65533;&#65533;ao&#65533;:&#65533;&#37084;&#65533;ib d&#1800;8&#65533;)&#65533;&#65533;d&#65533; &#65533;B&#65533;db &#65533;&#65533;ao&#65533;: &#65533; &#65533;,&#65533;&#65533;as&#65533;eÈ&#65533; &#65533;)
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : Premature end of data in tag long line 271
&#65533;&#65533;ao&#65533;:&#65533;&#37084;&#65533;ib d&#1800;8&#65533;)&#65533;&#65533;d&#65533; &#65533;B&#65533;db &#65533;&#65533;ao&#65533;: &#65533; &#65533;,&#65533;&#65533;as&#65533;eÈ&#65533; &#65533;)&#65533;d&#65533;&#65533;ao&#65533;&#65533;&#65533;th &#65533;&#65533;aoT50
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : Premature end of data in tag locale line 269
&#65533;&#65533;ao&#65533;:&#65533;&#37084;&#65533;ib d&#1800;8&#65533;)&#65533;&#65533;d&#65533; &#65533;B&#65533;db &#65533;&#65533;ao&#65533;: &#65533; &#65533;,&#65533;&#65533;as&#65533;eÈ&#65533; &#65533;)&#65533;d&#65533;&#65533;ao&#65533;&#65533;&#65533;th &#65533;&#65533;aoT50
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : Premature end of data in tag schema line 4
&#65533;&#65533;ao&#65533;:&#65533;&#37084;&#65533;ib d&#1800;8&#65533;)&#65533;&#65533;d&#65533; &#65533;B&#65533;db &#65533;&#65533;ao&#65533;: &#65533; &#65533;,&#65533;&#65533;as&#65533;eÈ&#65533; &#65533;)&#65533;d&#65533;&#65533;ao&#65533;&#65533;&#65533;th &#65533;&#65533;aoT50
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : Premature end of data in tag schemalist line 2
&#65533;&#65533;ao&#65533;:&#65533;&#37084;&#65533;ib d&#1800;8&#65533;)&#65533;&#65533;d&#65533; &#65533;B&#65533;db &#65533;&#65533;ao&#65533;: &#65533; &#65533;,&#65533;&#65533;as&#65533;eÈ&#65533; &#65533;)&#65533;d&#65533;&#65533;ao&#65533;&#65533;&#65533;th &#65533;&#65533;aoT50
                                                                               ^
/usr/share/gconf/schemas/netstatus.schemas:273: parser error : Premature end of data in tag gconfschemafile line 1
&#65533;&#65533;ao&#65533;:&#65533;&#37084;&#65533;ib d&#1800;8&#65533;)&#65533;&#65533;d&#65533; &#65533;B&#65533;db &#65533;&#65533;ao&#65533;: &#65533; &#65533;,&#65533;&#65533;as&#65533;eÈ&#65533; &#65533;)&#65533;d&#65533;&#65533;ao&#65533;&#65533;&#65533;th &#65533;&#65533;aoT50
                                                                               ^
dpkg: error processing gnome-netstatus-applet (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gnome-netstatus-applet
E: Sub-process /usr/bin/dpkg returned an error code (1)


Here're some more errors when using synaptic:

> E: gnome-netstatus-applet: subprocess post-installation script returned error exit status 1
E: system-config-printer: subprocess post-installation script returned error exit status 1
E: ubuntu-desktop: dependency problems - leaving unconfigured
E: xubuntu-desktop: dependency problems - leaving unconfigured


Any ideas guys? Would appreciate the help.

---

