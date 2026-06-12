---
title: "how to delete files from 'trash' that requires permission"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by j_evenstar on 2007-05-16
how do i do this? and how do i also delete other files from other directories that need permission? i've unintentionally copied my Desktop in a certain directory, and i fear that if i type sudo rm Desktop or sudo rm -rf Desktop, all will be lost..

help..

---

### Post by heimo on 2007-05-16
For not being able to remove some files from Trash, try:
```
chown -R $USER:$USER ~/.Trash
```

---

### Post by j_evenstar on 2007-05-16
> **heimo said:**
> For not being able to remove some files from Trash, try:
```
chown -R $USER:$USER ~/.Trash
```

long list of errors!!

```
-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libmozabdrv2.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libmysql2.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libmysql2.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libodbc2.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libodbc2.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libodbcbase2.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libodbcbase2.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libofficebean.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libofficebean.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libpackage2.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libpackage2.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libportaudio.so.0.0.18': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/librecentfile.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/librecentfile.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libreg.so.3': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libreg.so.3.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/librmcxt.so.3': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/librmcxt.so.3.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libscriptframe.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libscriptframe.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libsdbc2.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libsdbc2.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libsndfile.so.1.0.9': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libsrtrs1.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libsrtrs1.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libstdc++.so.6': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libstlport_gcc.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libstore.so.3': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libstore.so.3.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libtextconv_dict.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libtextconv_dict.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libtvhlp1.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libtvhlp1.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucb1.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucb1.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucbhelper3gcc3.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucbhelper3gcc3.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucpchelp1.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucpchelp1.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucpdav1.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucpdav1.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucpfile1.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucpfile1.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucpftp1.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucpftp1.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucphier1.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucphier1.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucppkg1.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libucppkg1.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libuno_cppu.so.3': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libuno_cppu.so.3.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libuno_cppuhelpergcc3.so.3': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libuno_cppuhelpergcc3.so.3.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libuno_sal.so.3': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libuno_sal.so.3.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libuno_salhelpergcc3.so.3': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libuno_salhelpergcc3.so.3.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libunoxml680li.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libunoxml680li.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libupdchk680li.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libupdchk680li.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/liburp_uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/liburp_uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libvos3gcc3.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libvos3gcc3.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libxml2.so.2.6.17': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libxmlsec1-nss.so.1.2.6': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libxmlsec1-nss.so.1.2.6.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libxmlsec1.so.1.2.6': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libxmlsecurity.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libxmlsecurity.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libxsec_fw.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libxsec_fw.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libxsec_xmlsec.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libxsec_xmlsec.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libxstor.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/libxstor.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/localebe1.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/localebe1.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/migrationoo2.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/migrationoo2.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/namingservice.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/namingservice.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/nestedreg.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/nestedreg.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/passwordcontainer.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/passwordcontainer.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/productregistration.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/productregistration.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/proxyfac.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/proxyfac.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/reflection.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/reflection.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/regtypeprov.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/regtypeprov.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/remotebridge.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/remotebridge.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/root5.dat': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/sax.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/sax.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/security.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/security.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/servicemgr.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/servicemgr.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/shlibloader.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/shlibloader.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/simplereg.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/simplereg.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/slideshow.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/slideshow.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/streams.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/streams.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/stringresource680li.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/stringresource680li.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/sunjavaplugin.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/sunjavaplugin.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/svtmisc.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/svtmisc.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/sysmgr1.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/sysmgr1.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/syssh.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/syssh.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/textinstream.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/textinstream.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/textoutstream.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/textoutstream.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/typeconverter.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/typeconverter.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/typemgr.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/typemgr.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/ucpexpand1.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/ucpexpand1.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/ucptdoc1.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/ucptdoc1.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/updatefeed.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/updatefeed.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/uriproc.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/uriproc.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/uuresolver.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/uuresolver.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/vclcanvas.uno.so': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program/vclcanvas.uno.so.1.1': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2/program': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt/openoffice.org2.2': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/opt': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/DEBIAN/shlibs': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/DEBIAN/postinst': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/DEBIAN/postrm': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/DEBIAN/md5sums': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/DEBIAN/control': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u/DEBIAN': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u.postinst.debhelper': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u.postrm.debhelper': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/files': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian/openoffice.org-core05u.substvars': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0/debian': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u-2.2.0': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-base_2.2.0-9135_i386.deb': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-calc_2.2.0-9135_i386.deb': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core01_2.2.0-9135_i386.deb': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core02_2.2.0-9135_i386.deb': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core03_2.2.0-9135_i386.deb': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core03u_2.2.0-9135_i386.deb': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core04_2.2.0-9135_i386.deb': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core04u_2.2.0-9135_i386.deb': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05_2.2.0-9135_i386.deb': Operation not permitted
chown: changing ownership of `/home/jillian/.Trash/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core05u_2.2.0-9135_i386.deb': Operation not permitted
jillian@jillian-desktop:~$

```

typing 
```
sudo chown -R $USER:$USER ~/.Trash
```
didn't produce any error but didn't delete the trash files.

---

### Post by carlosqueso on 2007-05-16
you need to use ```
sudo chown -R $USER:$USER ~/.Trash
```

---

### Post by heimo on 2007-05-16
> **j_evenstar said:**
> 
```
sudo chown -R $USER:$USER ~/.Trash
```didn't produce any error but didn't delete the trash files.


Yeah, I forgot the sudo. And no, it wasn't supposed to delete files, just change permissions(*. You can now try emptying trash the way you'd do it normally.

*) More specifically - **ch**ange the **own**er of the files.

---

### Post by j_evenstar on 2007-05-16
okay, thank you. i was able to empty it :)

---

### Post by heimo on 2007-05-16
> **j_evenstar said:**
> okay, thank you. i was able to empty it :)

Good. About the second part of your question, it'd be helpful to get more details. But if those are your personal files and not something that was installed by package management or install CD for instance, and for some reason you can't remove those files, you could probably adjust the command that was used to change ownership of the files for ~/.Trash.  -R flag makes the command recursive - meaning that everything under that folder will change ownership. **DO NOT** change ownership of any system files or your system will probably be badly messed.

---

### Post by jmate24 on 2008-03-15
i got nothing. when trying your trick i used ctrl-h to find my trash folder and there was nothing there but looking at my icon and opening the trash folder from my desktop icon and panel icon there are things in the trash! what do i do next. i am using hardy and here are the pics:

---

