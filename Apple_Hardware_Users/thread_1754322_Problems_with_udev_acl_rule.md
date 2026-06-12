---
title: "Problems with udev acl rule"
date: 2011-05-09
forum: Apple Hardware Users
---

### Post by nokangaroo on 2011-05-09
I am trying to create a udev rule that will allow me to mount an ext4 disk with acl option while preserving user unmountability. The following rule (adapted from [https://wiki.archlinux.org/index.php/Udev#About_udev_rules](https://wiki.archlinux.org/index.php/Udev#About_udev_rules)) will work, but I have to unmount the volume partition by partition; there is no &quot;Safely remove drive&quot;. Adding myself to the &quot;disk&quot; group won't work either, or changing device node permissions. I also tried using pmount, but that has no acl option and is therefore useless.

# Leave sda to fstab
KERNEL!=&quot;sd[b-z]*&quot;, GOTO=&quot;media_by_label_auto_mount_end&quot;

# We are handling only ext4 partitions
ENV{ID_FS_TYPE}!=&quot;ext4&quot;, GOTO=&quot;media_by_label_auto_mount_end&quot;

# Import FS info
IMPORT{program}=&quot;/sbin/blkid -o udev -p %N&quot;

# Get a label if present, otherwise specify one
ENV{ID_FS_LABEL}!=&quot;&quot;, ENV{dir_name}=&quot;%E{ID_FS_LABEL}&quot;
ENV{ID_FS_LABEL}==&quot;&quot;, ENV{dir_name}=&quot;usbhd-%k&quot;

# Mount options
ACTION==&quot;add&quot;, ENV{mount_options}=&quot;nodev,nosuid,relatime,acl,uhelper=udisks&quot;

# Mount the device
ACTION==&quot;add&quot;, RUN+=&quot;/bin/mkdir -p /media/%E{dir_name}&quot;, RUN+=&quot;/bin/mount -t %E{ID_FS_TYPE} -o %E{mount_options} /dev/%k /media/%E{dir_name}&quot;

# Clean up after removal
ACTION==&quot;remove&quot;, ENV{dir_name}!=&quot;&quot;, RUN+=&quot;/bin/umount -l /media/%E{dir_name}&quot;, RUN+=&quot;/bin/rmdir /media/%E{dir_name}&quot;

# Exit
LABEL=&quot;media_by_label_auto_mount_end&quot;

This works when copied to /etc/udev/rules.d/11-some-name.rules or /etc/udev/user.rules (the exact number does not seem to matter much), but unmounting as user does not work, also the devices appear twice in the nautilus side pane (a sure sign that something is fishy). Does udev use mount at all by default? And what else is there?

The file /lib/udev/rules.d/50-udev-default.rules does not seem to have a KERNEL==&quot;sd*&quot; entry at all, so maybe that's the problem. A half-solution is to add a mount -o remount,acl line to my backup scripts, but mount will hang when another program is accessing the disk.

Another problem is that the entries in /media will remain if the disk is unmounted but not actually unplugged, which will cause my backup scripts to fill up the root partition (this never happens with the default udev setup. Of course I could rewrite the scripts if necessary, but I'd rather fix this behaviour).

I am using ubuntu maverick with kernel 2.6.35-29-generic.

Sorry, tried to edit the uhel per, did not work. Should be &quot;uhelper&quot;

---

