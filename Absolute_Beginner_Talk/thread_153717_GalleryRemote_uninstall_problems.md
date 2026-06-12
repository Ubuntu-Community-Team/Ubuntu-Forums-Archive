---
title: "GalleryRemote uninstall problems"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by veighjay on 2006-04-01
hi

i tried installing GalleryRemote, and it is not working. I think this is because I put in the incorrect path to the java file (which is another story, something else I need to sort out another time). As a result, I want to uninstall (so i can try again). but when i go into the 'Uninstaller Data' folder in the GalleryRemote folder, and run the uninstall shell script, i get the following error:

'Fatal application error. this application has unexpectedly quit. invocation of this java application has caused an InvocationTargetException. this application will now exit (LAX).'

if i click on 'details', this is what comes up:

ava.lang.IllegalArgumentException: No product for ID=e14b382f-1ec1-11b2-9884-e8890d15c314
	at ZeroGev.<init>(DashoA8113)
	at com.zerog.ia.installer.Installer.q(DashoA8113)
	at com.zerog.ia.installer.Installer.p(DashoA8113)
	at com.zerog.ia.installer.Installer.setMetadata(DashoA8113)
	at com.zerog.ia.installer.InstallerMetaData.setInstaller(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.i(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
	at com.zerog.ia.installer.Main.main(DashoA8113)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.zerog.lax.LAX.launch(DashoA8113)
	at com.zerog.lax.LAX.main(DashoA8113)


anyone know what that means? anyone know how i can uninstall galleryremote? can i just delete the files?

thanks for your help....

---

### Post by veighjay on 2006-04-02
anyone?

---

### Post by alfredhitzkopf on 2006-07-31
:) got the same problem but no solution unfortunately. If I get an answer ill tell you.

---

### Post by catlett on 2006-07-31
What kind of package was it? Was it a tar file with an install script inside? Or was it a deb file?
If it was an install script, you can manually delete it's data. There aren't any registry keys like windows or anything. All the files may be in the single folder from the tar or it may have installed a binary into /usr/bin.
If it was a deb you should use dpkg -r deb.file nut you can just delete the binary and library if that is all that it is.
Do you have a link to the package you are trying to install.

---

