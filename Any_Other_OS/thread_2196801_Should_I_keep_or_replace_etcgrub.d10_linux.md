---
title: "Should I keep or replace /etc/grub.d/10_linux?"
date: 2013-12-31
forum: Any Other OS
---

### Post by palawanbeach on 2013-12-31
I ran the Update Manager (on Linux Mint) and I'm asked to decide whether to keep my current file or replace it. Please help.


Here's the difference between the files.

--- /etc/grub.d/10_linux	2013-12-31 13:55:18.791974218 +0800
+++ /etc/grub.d/10_linux.dpkg-new	2013-12-06 18:06:55.000000000 +0800
@@ -82,13 +82,13 @@
   version="$2"
   recovery="$3"
   args="$4"
-  description="`grep GRUB_TITLE /etc/linuxmint/info | awk -F = '{print $2}'`"
   if ${recovery} ; then
-    title="${description}, ${version} (${GRUB_DEVICE_BOOT}) -- recovery mode"
+    title="$(gettext_quoted "%s, with Linux %s (%s)")"
+    printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}" "$(gettext "${GRUB_RECOVERY_TITLE}")"
   else
-    title="${description}, ${version} (${GRUB_DEVICE_BOOT})"
+    title="$(gettext_quoted "%s, with Linux %s")"
+    printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
   fi
-  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
   cat << EOF
 	recordfail
 EOF
@@ -121,9 +121,15 @@
 	echo	'$message'
 EOF
   fi
-  cat << EOF
+  if test -d /sys/firmware/efi && test -e "${linux}.efi.signed"; then
+    cat << EOF
+	linux	${rel_dirname}/${basename}.efi.signed root=${linux_root_device_thisversion} ro ${args}
+EOF
+  else
+    cat << EOF
 	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
 EOF
+  fi
   if test -n "${initrd}" ; then
     if [ "x$5" != "xquiet" ]; then
       message="$(gettext_printf "Loading initial ramdisk ...")"
@@ -156,8 +162,8 @@
 
 cat << 'EOF'
 function gfxmode {
-	set gfxpayload="$1"
-	if [ "$1" = "keep" ]; then
+	set gfxpayload="${1}"
+	if [ "${1}" = "keep" ]; then
 		set vt_handoff=vt.handoff=7
 	else
 		set vt_handoff=
@@ -171,7 +177,7 @@
   echo "set linux_gfx_mode=$GRUB_GFXPAYLOAD_LINUX"
 else
   cat << EOF
-if [ \${recordfail} != 1 ]; then
+if [ "\${recordfail}" != 1 ]; then
   if [ -e \${prefix}/gfxblacklist.txt ]; then
     if hwmatch \${prefix}/gfxblacklist.txt 3; then
       if [ \${match} = 0 ]; then
@@ -192,12 +198,19 @@
 fi
 cat << EOF
 export linux_gfx_mode
-if [ "\$linux_gfx_mode" != "text" ]; then load_video; fi
+if [ "\${linux_gfx_mode}" != "text" ]; then load_video; fi
 EOF
 
 in_submenu=false
 while [ "x$list" != "x" ] ; do
   linux=`version_find_latest $list`
+  case $linux in
+    *.efi.signed)
+      # We handle these in linux_entry.
+      list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
+      continue
+      ;;
+  esac
   echo "Found linux image: $linux" >&2
   basename=`basename $linux`
   dirname=`dirname $linux`

---

### Post by deadflowr on 2013-12-31
I always choose replace.
But don't use mint so don't know what craziness would ensue.
Don't think anything bad would happen.
In fact I'm pretty sure it'll be fine.
Unless you've done some extensive editing to the file.

If you're worried copy the existing one somewhere safe just in case.

I, though, never had a problem with replacing it.
Of course, for me, this issue is moot now, since I use a custom grub setup.

---

### Post by palawanbeach on 2013-12-31
deadflowr,
Thanks for your reply. I made a copy of the original file and chose "Replace".

---

