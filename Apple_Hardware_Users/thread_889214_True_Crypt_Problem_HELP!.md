---
title: "True Crypt Problem HELP!"
date: 2008-08-13
forum: Apple Hardware Users
---

### Post by estranged1977 on 2008-08-13
Hi, Im using ubuntu 8.04 powerpc, things goes nice but I can't find how to mount TrueCrypt volumes, I tried to install truecrypt but theres not a binary for PPC, I downloaded de source but it ask for wxwidgets and it also cannot be installed, or it doesn't install the files needed.

So my question is how to do it, I have a lot of info encrypted in truecrypt volumes, so my problem is big, is there any application to open this files?
I tried to with cryptmount but it appears "target xxxx is not recognized".

What can I do?

---

### Post by cyberdork33 on 2008-08-14
I think the older versions had a commandline utility. That is probably your best bet.


PS You have to put commas between your tags.

---

### Post by estranged1977 on 2008-08-15
Ok, thanks for the idea, I just did it like if where under X86, I downloaded truecrypt source [http://www.truecrypt.org/downloads2.php]("http://www.truecrypt.org/downloads2.php") (have to select for linux tar.gz format), then download wxwidgets 2.8.8 [http://prdownloads.sourceforge.net/wxwindows/wxWidgets-2.8.8.tar.gz]("http://prdownloads.sourceforge.net/wxwindows/wxWidgets-2.8.8.tar.gz") , decompress both:
```

$ tar xzvf TrueCrypt 6.0 Source.tar.gz
$ tar xzvf wxWidgets-2.8.8.tar.gz

```
and did the following:
```

$ cd truecrypt-6.0-source
$ make WX_ROOT=[directory where decompressed wxWidgets]wxWidgets-2.8.8 wxbuild

```
and finally,
```

$ make

```
Then we can enter to Main directory;
```

$ cd Main

```
And and last truecrypt workin' 
```

$ ./truecrypt

```

Thats all, it runs very good!!!

---

### Post by cyberdork33 on 2008-08-15
ah I see now... You could also just search the apt databaase for the appropriate -dev package.

I think this is it:
```
sudo apt-get install libwxgtk2.8-dev
```

---

### Post by youfudoij on 2008-08-17
:lolflag:it is an unearthly world. There are all kinds of character. Some of them like promenade. Obtain delight in this far-flung course. Others like assault .fight the enemy. You could find interesting in slow journey.  Step by step. You also could leap in a short time by use safety powerleveling.
[www.8thgame.com](www.8thgame.com) provide safety pl. their gold is cheapeast also.

---

### Post by FaiSua on 2009-02-21
I am also trying to get TrueCrypt working on power pc, I tried both of these suggestions and didn't have any result.

The download page is not working for the source code, and I tried the other packages and still get the same message.

"error wrong architecture i386"

Is there a command to download the source code from the terminal?

---

### Post by cyberdork33 on 2009-02-21
> **FaiSua said:**
> Is there a command to download the source code from the terminal?
If it is in the ubuntu repos, you can usually get things like:
```
sudo apt-get source packagename
```I downloaded the source just fine from the website though. I mirrored the source package on my site if you'd rather:
[http://www.rickycampbell.com/Ubuntu/TrueCrypt 6.1a Source.tar.gz]("http://www.rickycampbell.com/Ubuntu/TrueCrypt%206.1a%20Source.tar.gz")

---

### Post by FaiSua on 2009-02-21
I got the two files extracted to my desktop. Then I changed to the extracted truecrypt-6.1a-source directory and typed
$ make WX_ROOT=/Desktop/wxWidgets-2.8.8/build 
Then I recieved these errors after a whole bunch of compiling:

[SIZE="2"]shambu@shambu-laptop:~/Desktop/truecrypt-6.1a-source$  make WX_ROOT=/Desktop/wxWidgets-2.8.8/build
Compiling Buffer.cpp
Compiling Exception.cpp
Compiling Event.cpp
Compiling FileCommon.cpp
Compiling MemoryStream.cpp
Compiling Memory.cpp
Compiling PlatformTest.cpp
Compiling Serializable.cpp
Compiling Serializer.cpp
Compiling SerializerFactory.cpp
Compiling StringConverter.cpp
Compiling TextReader.cpp
Compiling Directory.cpp
Compiling File.cpp
Compiling FilesystemPath.cpp
Compiling Mutex.cpp
Compiling Pipe.cpp
Compiling Poller.cpp
Compiling Process.cpp
Compiling SyncEvent.cpp
Compiling SystemException.cpp
Compiling SystemInfo.cpp
Compiling SystemLog.cpp
Compiling Thread.cpp
Compiling Time.cpp
Updating library Platform.a
Compiling Cipher.cpp
Compiling EncryptionAlgorithm.cpp
Compiling EncryptionMode.cpp
Compiling EncryptionModeCBC.cpp
Compiling EncryptionModeLRW.cpp
Compiling EncryptionModeXTS.cpp
Compiling EncryptionTest.cpp
Compiling EncryptionThreadPool.cpp
Compiling Hash.cpp
Compiling Keyfile.cpp
In file included from Keyfile.cpp:10:
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:43:21: warning: pkcs11.h: No such file or directory
In file included from Keyfile.cpp:10:
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:56: error: ‘CK_SLOT_ID’ does not name a type
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:57: error: ‘CK_FLAGS’ does not name a type
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:77: error: ‘CK_OBJECT_HANDLE’ does not name a type
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:80: error: ‘CK_SLOT_ID’ does not name a type
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:86: error: expected `)' before ‘errorCode’
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:92: error: expected `)' before ‘errorCode’
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:106: error: ‘CK_RV’ does not name a type
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:109: error: ‘CK_RV’ does not name a type
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:160: error: ‘CK_SESSION_HANDLE’ does not name a type
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:181: error: ‘CK_SLOT_ID’ has not been declared
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:183: error: ‘CK_SLOT_ID’ has not been declared
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:186: error: ‘CK_SLOT_ID’ has not been declared
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:194: error: ‘CK_SLOT_ID’ has not been declared
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:195: error: ‘CK_OBJECT_HANDLE’ was not declared in this scope
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:195: error: template argument 1 is invalid
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:195: error: template argument 2 is invalid
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:195: error: ‘CK_SLOT_ID’ has not been declared
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:195: error: ‘CK_ATTRIBUTE_TYPE’ has not been declared
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:196: error: ‘CK_SLOT_ID’ has not been declared
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:196: error: ‘CK_OBJECT_HANDLE’ has not been declared
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:196: error: ‘CK_ATTRIBUTE_TYPE’ has not been declared
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:197: error: ‘CK_SLOT_ID’ was not declared in this scope
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:197: error: template argument 1 is invalid
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:197: error: template argument 2 is invalid
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:198: error: ‘CK_SLOT_ID’ has not been declared
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:199: error: ‘CK_SLOT_ID’ has not been declared
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:200: error: ‘CK_SLOT_ID’ has not been declared
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:205: error: ‘CK_FUNCTION_LIST_PTR’ does not name a type
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:211: error: ‘CK_SLOT_ID’ was not declared in this scope
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:211: error: template argument 1 is invalid
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:211: error: template argument 3 is invalid
/home/shambu/Desktop/truecrypt-6.1a-source/Common/SecurityToken.h:211: error: template argument 4 is invalid
make[1]: *** [Keyfile.o] Error 1
make: *** [all] Error 2[/SIZE]

I am new to this so please bear with me. It sure is a lot of fun though

---

### Post by cyberdork33 on 2009-02-22
> **FaiSua said:**
> [SIZE=2]shambu@shambu-laptop:~/Desktop/truecrypt-6.1a-source$  make WX_ROOT=/Desktop/wxWidgets-2.8.8/build[/SIZE]
this command doesn't look right compared to the example.

It should be something like:
```
[SIZE=2]make WX_ROOT=/home/shambu/Desktop/wxWidgets-2.8.8[/SIZE] wxbuild
```See if you get the same error that way.

Looking at the error though, it sounds like the pkcs11 headers are missing, and looking at the TrueCrypt readme in the requirements for building on Linux:
[quote=TrueCrypt Readme]- RSA Security Inc. PKCS #11 Cryptographic Token Interface (Cryptoki) 2.20
  header files (available at [ftp://ftp.rsasecurity.com/pub/pkcs/pkcs-11/v2-20](ftp://ftp.rsasecurity.com/pub/pkcs/pkcs-11/v2-20))
  located in a standard include path or in a directory defined by the
  environment variable 'PKCS11_INC'.[/quote]

---

### Post by FaiSua on 2009-02-22
My bad, the code was wrong, thanks.
I am getting another error now. I will attempt to figure it out but right now I am in the dark. Any help is much appreciated.

shambu@shambu-laptop:~/Desktop/truecrypt-6.1a-source$ make WX_ROOT=/home/shambu/Desktop/wxWidgets-2.8.8 wxbuild
Configuring wxWidgets library...
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.
                            
make: *** [wxbuild] Error 1

---

### Post by cyberdork33 on 2009-02-22
> **FaiSua said:**
> My bad, the code was wrong, thanks.
I am getting another error now. I will attempt to figure it out but right now I am in the dark. Any help is much appreciated.

shambu@shambu-laptop:~/Desktop/truecrypt-6.1a-source$ make WX_ROOT=/home/shambu/Desktop/wxWidgets-2.8.8 wxbuild
Configuring wxWidgets library...
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.
                            
make: *** [wxbuild] Error 1
you will need the dev files for a bit of software. Typically, these packages have -dev on the end. So the gtk+ development files might be something like gtk+-2.0-dev or something. You will have to look in synaptic.

---

