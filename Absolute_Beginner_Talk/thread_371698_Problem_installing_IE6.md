---
title: "Problem installing IE6"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by gewitty on 2007-02-27
I was just trying to install IE6, following the instructions at [www.psychocats.net/ubuntu/ies4linux](www.psychocats.net/ubuntu/ies4linux).

I already had Wine and Cabextract installed, so just downloaded the IES4Linux package, extracted it and then ran it from terminal. Unfortunately, this failed whilst extracting the CAB files, but I don't know why. The relevant terminal text is shown below. If anyone can give me an idea of why this is happening, I'd be grateful.

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
/home/dave/.ies4linux/downloads/ie6/EN-US//ADVAUTH.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/dave/.ies4linux/downloads/ie6/EN-US//CRLUPD.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/dave/.ies4linux/downloads/ie6/EN-US//HHUPD.CAB: WARNING; possible 6720 extra bytes at end of file.
/home/dave/.ies4linux/downloads/ie6/EN-US//IEDOM.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_EXTRA.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_S1.CAB: WARNING; possible 1532565 extra bytes at end of file.
ie_1.cab: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_S2.CAB: WARNING; possible 1464965 extra bytes at end of file.
ie_2.cab: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_S3.CAB: WARNING; possible 1106151 extra bytes at end of file.
ie_3.cab: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_S4.CAB: WARNING; possible 1065607 extra bytes at end of file.
ie_4.cab: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_S5.CAB: WARNING; possible 761527 extra bytes at end of file.
ie_5.cab: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_S6.CAB: WARNING; possible 264823 extra bytes at end of file.
/home/dave/.ies4linux/downloads/ie6/EN-US//SCR56EN.CAB: WARNING; possible 776711 extra bytes at end of file.
jscript.dll: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//SETUPW95.CAB: WARNING; possible 733107 extra bytes at end of file.
cp_28595.nls: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//VGX.CAB: WARNING; possible 560603 extra bytes at end of file.
vgx.dll: checksum error
An error occured when trying to cabextract some files.

---

### Post by chggr on 2007-02-27
It is very rare to try and install a Windows application in linux through wine and succeed. 
Why stick on IE when there's Firefox, much better I think.

Furthermore, there are Firefox plugins that can open a web page as if IE6 was the web browser.

---

### Post by Jonne on 2007-02-27
I'd recommend running Windows in VMWare instead. 
I'm not sure why it didn't work for you though, I've done it successfully on another computer running Hoary a while back. Maybe the instructions are just outdated. 

The IE you end up with if you manage to get it work is far from useful, though. ActiveX won't work (so things like the transparent png hack and opacity filters don't work), and if you plan on using it to test web sites, you'll have to compare on Windows anyway just to make sure.

Get vmware player or vmware server (both are free), and install Windows on that. Windows XP can run (not install, run) if you only give it 32MB ram (though I'd recommend 64MB if you can afford it).

---

### Post by EvilMarshmallow on 2007-02-27
chggr,

Can you provide a link to that plugin you're talking about?  My wife is taking online courses through a local college and some of the stuff requires IE to run.  It's the only reason she hasn't switched to Ubuntu.

I searched on the mozilla website but the only one I found required IE > 4 to be installed already, and opened it in a Firefox tab.

---

### Post by Brunellus on 2007-02-27
> **gewitty said:**
> I was just trying to install IE6, following the instructions at [www.psychocats.net/ubuntu/ies4linux](www.psychocats.net/ubuntu/ies4linux).

I already had Wine and Cabextract installed, so just downloaded the IES4Linux package, extracted it and then ran it from terminal. Unfortunately, this failed whilst extracting the CAB files, but I don't know why. The relevant terminal text is shown below. If anyone can give me an idea of why this is happening, I'd be grateful.

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
/home/dave/.ies4linux/downloads/ie6/EN-US//ADVAUTH.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/dave/.ies4linux/downloads/ie6/EN-US//CRLUPD.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/dave/.ies4linux/downloads/ie6/EN-US//HHUPD.CAB: WARNING; possible 6720 extra bytes at end of file.
/home/dave/.ies4linux/downloads/ie6/EN-US//IEDOM.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_EXTRA.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_S1.CAB: WARNING; possible 1532565 extra bytes at end of file.
ie_1.cab: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_S2.CAB: WARNING; possible 1464965 extra bytes at end of file.
ie_2.cab: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_S3.CAB: WARNING; possible 1106151 extra bytes at end of file.
ie_3.cab: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_S4.CAB: WARNING; possible 1065607 extra bytes at end of file.
ie_4.cab: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_S5.CAB: WARNING; possible 761527 extra bytes at end of file.
ie_5.cab: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//IE_S6.CAB: WARNING; possible 264823 extra bytes at end of file.
/home/dave/.ies4linux/downloads/ie6/EN-US//SCR56EN.CAB: WARNING; possible 776711 extra bytes at end of file.
jscript.dll: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//SETUPW95.CAB: WARNING; possible 733107 extra bytes at end of file.
cp_28595.nls: checksum error
/home/dave/.ies4linux/downloads/ie6/EN-US//VGX.CAB: WARNING; possible 560603 extra bytes at end of file.
vgx.dll: checksum error
An error occured when trying to cabextract some files.
it would appear that the download was somehow corrupted.  delete the IEs4Linux installer script, re-download, and try again.

---

### Post by gewitty on 2007-02-27
Thanks for all the advice. I only need IE to check the appearance of various web sites. Firefox is my standard browser of choice. I'll try deleting the original download and then give it another go.

---

### Post by stoshb on 2007-02-27
I have seen elsewhere that under current Wine you don't install that IES4Linux package module.

I am trying to install MSMoney, which needs IE6, and am getting:


stan@Dilbert:~/Desktop$ wine ie6setup
fixme:advapi:CheckTokenMembership ((nil) 0x162f58 0x32fd78) stub!
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advpack:NeedReboot (0): stub
fixme:crypt:I_CryptInstallOssGlobal 60d0c180 00000000 00000000, return value 9
fixme:crypt:I_CryptInstallOssGlobal 4760d950 00000000 00000000, return value 10
fixme:crypt:CryptSIPLoad ({c689aab8-8e78-11d0-8c47-00c04fc295ee} 0 0x1ad460) stub!
fixme:crypt:CryptSIPLoad ({c689aab8-8e78-11d0-8c47-00c04fc295ee} 0 0x18c120) stub!
fixme:advpack:FileSaveRestoreW (0x100f2, L"c:\\windows\\Help\\APPS.HLP", L"C:\\Program Files\\Internet Explorer\\", L"ie6bak", 24) stub
fixme:crypt:CertEnumCTLsInStore (0x168f10, (nil)): stub
stan@Dilbert:~/Desktop$ 

The install downloads trying to install the first module from the internet.

Any suggestions? (and I know don't use IE.  I don't on a daily basis, just need it for my MSMoney process)

---

### Post by stoshb on 2007-02-27
Found problem.  Needed to set my Wine Default to Windows XP.  Then it all worked.

---

### Post by hardyn on 2007-02-27
somebody just posed a deb.... maybe it will work for you.

[http://www.ubuntuforums.org/showthread.php?t=370705](http://www.ubuntuforums.org/showthread.php?t=370705)

---

### Post by chggr on 2007-02-28
I was talking about this: [https://addons.mozilla.org/firefox/1419/](https://addons.mozilla.org/firefox/1419/)

But it appears that this extention is only available in Windows :(

---

