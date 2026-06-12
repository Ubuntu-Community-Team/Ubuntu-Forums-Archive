---
title: "Installing KDE on Ubuntu"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by TiLaser on 2007-12-31
I'm trying to install KDE on Ubuntu.  I followed the instructions at [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE) using Synaptics to install the packages.  Halfway through the download my connection cut out.  I restarted began the install again.  Eventually it came up with the error

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I try 'dpkg --configure -a' I get

> jbarrus@jbarruslaptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up tex-common (1.9) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing tex-common (--configure):
 subprocess post-installation script returned error exit status 127
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exjbarrus@jbarruslaptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up tex-common (1.9) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing tex-common (--configure):
 subprocess post-installation script returned error exit status 127
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1
it status 1


I appreciate your help.

---

### Post by snakeeyes on 2007-12-31
what is the output of:
sudo apt-get install kubuntu-desktop

---

### Post by TiLaser on 2007-12-31
-
> jbarrus@jbarruslaptop:~$ sudo apt-get install kubuntu-desktop
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


Is it possible to clear whatever it is having problems with and start again?

---

### Post by snakeeyes on 2007-12-31
run:
sudo dpkg --configure -a
tell me the output of that, I haven't seen that message before, but lets see.

---

### Post by p_quarles on 2007-12-31
> **snakeeyes said:**
> run:
sudo dpkg --configure -a
tell me the output of that, I haven't seen that message before, but lets see.
The output of that is in the first message.

@TiLaser: Looks like the problem is with initramfs; it's not updating. Let's try to get some more information about why:
```
sudo update-initramfs -u
```

---

### Post by forestpixie on 2007-12-31
it's in his first post - if he 's a he if not sorry

not sure if this will help - but try, post output here

```
sudo apt-get install -f
```

in the meantime I'd be inclined to not turn it off

Edit - that'll be better - I've no idea about 'sudo update-initramfs -u' just didn't want you to turn it off justin case

---

### Post by snakeeyes on 2007-12-31
also try to clear out broken packages, go in to synaptic and check if any packages r broken and also run the commands:
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean

---

### Post by TiLaser on 2007-12-31
-
> jbarrus@jbarruslaptop:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
jbarrus@jbarruslaptop:~$ 

> jbarrus@jbarruslaptop:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

> jbarrus@jbarruslaptop:~$ sudo apt-get autoremove
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jbarrus@jbarruslaptop:~$ sudo apt-get autoclean
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jbarrus@jbarruslaptop:~$ sudo apt-get clean


---

### Post by snakeeyes on 2007-12-31
try going in Synaptic and at the bottom u should see the number of packages installed, broken, or upgradeable and tell us what it shows.

---

### Post by p_quarles on 2007-12-31
```
jbarrus@jbarruslaptop:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
```
Hmm. Same message. Can you post the output of this:
```
cat /usr/sbin/mkinitramfs
```
If nothing else, I can compare it to the (working) script on my system, and see if perhaps there's a syntax error in there.

---

### Post by TiLaser on 2007-12-31
Snakeeyes, I cannot open Synaptics.  The error message appears at start up.

> jbarrus@jbarruslaptop:~$ cat /usr/sbin/mkinitramfs
#!/bin/sh

umask 0022

# Defaults
keep="n"
CONFDIR="/etc/initramfs-tools"
verbose="n"
errors_to="2>/dev/null"
BUSYBOXDIR="/usr/lib/initramfs-tools/bin/"
# BUSYBOXDIR="/bin"

OPTIONS=`getopt -o d:ko:r:v --long supported-host-version:,supported-target-version: -n "$0" -- "$@"`

# Check for non-GNU getopt
if [ $? != 0 ] ; then echo "Terminating..." >&2 ; exit 1 ; fi

eval set -- "$OPTIONS"

while true; do
        case "$1" in
        -d)
                CONFDIR="$2"
                shift 2
                if [ ! -d "${CONFDIR}" ]; then
                        echo "${0}: ${CONFDIR}: Not a directory" >&2
                        exit 1
                fi
                ;;
        -o)
                outfile="$2"
                shift 2
                ;;
        -k)
                keep="y"
                shift
                ;;
        -r)
                ROOT="$2"
                shift 2
                ;;
        -v)
                verbose="y"
                shift
                ;;
        --supported-host-version)
                supported_host_version="$2"
                shift 2
                ;;
        --supported-target-version)
                supported_target_version="$2"
                shift 2
                ;;
        --)
                shift
                break
                ;;
        *)
                echo "Internal error!" >&2
                exit 1
                ;;
        esac
done

if [ -n "$supported_host_version" ] || [ -n "$supported_target_version" ]; then
        if [ -n "$supported_host_version" ]; then
                host_upstream_version="${supported_host_version%%-*}"
        fi
        if [ -n "$supported_target_version" ]; then
                target_upstream_version="${supported_target_version%%-*}"
                if dpkg --compare-versions "$target_upstream_version" lt "2.6.12"; then
                        exit 2
                fi
        fi
        echo "Depreciation warning: use ramdisk=mkinitramfs-kpkg."
        exit 0
fi

# For dependency ordered mkinitramfs hook scripts.
. /usr/share/initramfs-tools/scripts/functions
. /usr/share/initramfs-tools/hook-functions

. "${CONFDIR}/initramfs.conf"
EXTRA_CONF=''
for i in /usr/share/initramfs-tools/conf.d/* ${CONFDIR}/conf.d/*; do
        EXTRA_CONF="${EXTRA_CONF} $(basename $i | grep '^[a-z0-9][a-z0-9\._-]*$' | grep -v '\.dpkg-.*$')";
done
for i in ${EXTRA_CONF}; do
        if [ -e  ${CONFDIR}/conf.d/${i} ]; then
                . ${CONFDIR}/conf.d/${i}
        elif [ -e  /usr/share/initramfs-tools/conf.d/${i} ]; then
                . /usr/share/initramfs-tools/conf.d/${i}
        fi
done

if [ -n "${UMASK}" ]; then
        umask "${UMASK}"
fi

if [ -z "${outfile}" ]; then
        usage
fi

touch "$outfile"
outfile="$(readlink -f "$outfile")"

# And by "version" we really mean path to kernel modules
# This is braindead, and exists to preserve the interface with mkinitrd
if [ ${#} -ne 1 ]; then
        version="$(uname -r)"
else
        version="${1}"
fi

# Check that we're using a new enough kernel version, first for ourselves,
# then for each of the hooks, which can have a MINKVER variable defined
check_minkver ${version}
check_minkver ${version} /usr/share/initramfs-tools/hooks
check_minkver ${version} ${CONFDIR}/hooks

case "${version}" in
/lib/modules/*/[!/]*)
        ;;
/lib/modules/[!/]*)
        version="${version#/lib/modules/}"
        version="${version%%/*}"
        ;;
esac

case "${version}" in
*/*)
        echo "$PROG: ${version} is not a valid kernel version" >&2
        exit 1
        ;;
esac

if [ -d "${outfile}" ]; then
        echo "${outfile} is a directory"
        exit 1
fi

MODULESDIR="/lib/modules/${version}"

if [ ! -e "${MODULESDIR}" ]; then
        echo "Cannot find ${MODULESDIR}"
        exit 1
fi
if [ ! -e "${MODULESDIR}/modules.dep" ]; then
        depmod ${version}
fi

DESTDIR="$(mktemp -t -d mkinitramfs_XXXXXX)" || exit 1
__TMPCPIOGZ="$(mktemp -t mkinitramfs-OL_XXXXXX)" || exit 1

DPKG_ARCH=`dpkg --print-installation-architecture`

# Export environment for hook scripts.
#
export MODULESDIR
export version
export CONFDIR
export DESTDIR
export DPKG_ARCH
export verbose

# Private, used by 'catenate_cpiogz'.
export __TMPCPIOGZ

for d in bin conf/conf.d etc lib modules sbin scripts ${MODULESDIR}; do
        mkdir -p "${DESTDIR}/${d}"
done

# MODULES=list case.  Always honour.
for x in "${CONFDIR}/modules" /usr/share/initramfs-tools/modules.d/*; do
        if [ -f "${x}" ]; then
                add_modules_from_file "${x}"
        fi
done

if [ "${MODULES}" = "dep" ]; then
        dep_add_modules
fi

if [ "${MODULES}" = "most" ]; then
        auto_add_modules
fi

if [ "${MODULES}" = "netboot" ]; then
        auto_add_modules base
        auto_add_modules net
fi

# Have to do each file, because cpio --dereference doesn't recurse down
# symlinks.

# klibc
ln -s /usr/lib/klibc/bin/* ${DESTDIR}/bin
ln -s /lib/klibc-*.so ${DESTDIR}/lib
copy_exec /usr/share/initramfs-tools/init /init
cp -a /usr/share/initramfs-tools/scripts/* "${DESTDIR}/scripts"
for f in $(cd ${CONFDIR}/scripts && \
        find . \( -name '*.dpkg*' -prune -o -name '*~' -prune \) \
                -o -type f -print); do
        mkdir --parents "${DESTDIR}/scripts/$(dirname "${f}")"
cp -p "${CONFDIR}/scripts/${f}" "${DESTDIR}/scripts/$(dirname "${f}")"
done
echo "DPKG_ARCH=${DPKG_ARCH}" > ${DESTDIR}/conf/arch.conf
copy_exec "${CONFDIR}/initramfs.conf" /conf
for i in ${EXTRA_CONF}; do
        if [ -e "${CONFDIR}/conf.d/${i}" ]; then
                copy_exec "${CONFDIR}/conf.d/${i}" /conf/conf.d
        elif [ -e "/usr/share/initramfs-tools/conf.d/${i}" ]; then
                copy_exec "/usr/share/initramfs-tools/conf.d/${i}" /conf/conf.d
        fi
done

# ROOT hardcoding
if [ -n "${ROOT}" ]; then
        echo "ROOT=${ROOT}" > ${DESTDIR}/conf/conf.d/root
fi

# Busybox
if [ "x${BUSYBOX}" = "xn" ]; then
        ln -s ${DESTDIR}/bin/sh.shared ${DESTDIR}/bin/sh
        echo "Warning: Busybox is required for successful boot!"
else
        rm -f ${DESTDIR}/bin/sh
        rm -f ${DESTDIR}/bin/busybox
        copy_exec ${BUSYBOXDIR}/busybox /bin/busybox
        ln -s ${BUSYBOXDIR}/busybox ${DESTDIR}/bin/sh
fi

# Modutils
copy_exec /sbin/modprobe /sbin
copy_exec /sbin/depmod /sbin
copy_exec /sbin/rmmod /sbin
mkdir -p "${DESTDIR}/etc/modprobe.d"
cp -a /etc/modprobe.d/* "${DESTDIR}/etc/modprobe.d"

run_scripts /usr/share/initramfs-tools/hooks
run_scripts "${CONFDIR}"/hooks

# FIXME: Remove this Raid block after Etch releases
if [ -x /sbin/mdadm ] && [ ! -f /usr/share/initramfs-tools/hooks/mdadm ]; then
        # use mkinitrd magic for Sarge backwards compat
        rootraiddev="$(df / | sed -rne 's,^(/dev/[^[:space:]]+).*,\1,p')"
        echo "rootraiddev=${rootraiddev}" > ${DESTDIR}/conf/mdrun.conf
        mdadm=$(mdadm --detail "${rootraiddev}")
        echo "${mdadm}" | awk '
                $1 == "Number" && $2 == "Major" { start = 1; next }
                $1 == "UUID" { print "uuid=" $3; next }
                !start { next }
                $2 == 0 && $3 == 0 { next }
                { devices = devices " " $NF }
                END { print "devices='\''" devices "'\''" }' \
                >> ${DESTDIR}/conf/mdrun.conf
        copy_exec /sbin/mdadm /sbin
        for x in md linear multipath raid0 raid1 raid456 raid5 raid6 raid10; do
                manual_add_modules ${x}
        done
fi
[ -x /sbin/mdrun ] && copy_exec /sbin/mdrun /sbin

# FIXME: Remove this LVM block after Etch releases
if [ -x /sbin/vgchange ] && [ -d /lib/lvm-200 ] \
        && [ ! -f /usr/share/initramfs-tools/hooks/lvm2 ]; then
        copy_exec /lib/lvm-200/vgchange /sbin
        for x in dm_mod dm_snapshot dm_mirror; do
                manual_add_modules ${x}
        done
fi

# Apply DSDT to initramfs
if [ -e "${CONFDIR}/DSDT.aml" ]; then
        copy_exec "${CONFDIR}/DSDT.aml" /
fi

[ "${verbose}" = y ] && echo "Building cpio ${outfile} initramfs"
(cd "${DESTDIR}" && find . | cpio --quiet --dereference -o -H newc | gzip -9 >"${outfile}") || exit 1

if [ -s "${__TMPCPIOGZ}" ]; then
        cat "${__TMPCPIOGZ}" >>"${outfile}" || exit 1
fi

if [ "${keep}" = "y" ]; then
        echo "Working files in ${DESTDIR} and overlay in ${__TMPCPIOGZ}"
else
        rm -rf "${DESTDIR}"
        rm -rf "${__TMPCPIOGZ}"
fi

exit 0


---

### Post by p_quarles on 2007-12-31
Okay, line 13 reads exactly as it should. Try this, and post the output:
```
getopt -V
```

---

### Post by snakeeyes on 2007-12-31
type in the kernel aptitude and see whether u can open that atleast.

---

### Post by TiLaser on 2007-12-31
-
> jbarrus@jbarruslaptop:~$ getopt -V
The program 'getopt' is currently not installed.  You can install it by typing:
sudo apt-get install util-linux
bash: getopt: command not found


---

### Post by p_quarles on 2007-12-31
> **snakeeyes said:**
> type in the kernel aptitude and see whether u can open that atleast.
snakeeyes, it's pretty clear at this point that the root problem is *not *with the package manager itself. 

> **TiLaser said:**
> ```
jbarrus@jbarruslaptop:~$ getopt -V
The program 'getopt' is currently not installed.  You can install it by typing:
sudo apt-get install util-linux
bash: getopt: command not found
```
Well, there's your problem then. Unfortunately, this could be a tough one to solve, since you're having trouble using the package manager without it. Give me a minute to do some reading, and I'll see if I can find a solution.

EDIT: One thing to do, in the meantime, is to get more information about the precise state of the getopt package:
```
dpkg --get-selections getopt
```
and
```
dpkg --get-selections util-linux
```

---

### Post by TiLaser on 2007-12-31
-
> jbarrus@jbarruslaptop:~$ dpkg --get-selections getopt
No packages found matching getopt.

> 
jbarrus@jbarruslaptop:~$ dpkg --get-selections util-linux
util-linux                                      install


---

### Post by snakeeyes on 2007-12-31
I know but I just wanted him to check which packages were broken first.

---

### Post by p_quarles on 2007-12-31
Okay, getopt isn't actually a separate package, so it shouldn't show up anyway. The point is that it seems to be missing from the util-linux package. This looks like it could be a sticky problem, but I can think of a couple things to try. First:
```
sudo dpkg-reconfigure util-linux
```
I'm *guessing *that this will result in an error code similar to what you've seen with other package management tools, but it's worth a shot.

The "last resort" option is to reinstall the package from source, which won't require your package manager to get involved, but this does come with its own risks. This is the best I can come up with at the moment, but I'd suggest waiting a bit to see if some kind person can stop by with a better idea.

Anyway, here's how to do it:
```
apt-get source util-linux
```
You *don't* need sudo with this, and hopefully it won't give you any errors. If it does, you'll need to manually download the source package. After that, you can cd into the unpacked util-linux-2.13 directory, and run the following:
```
./configure
make
sudo make install
```
You can go ahead and get the source code now, but like I said, wait a bit to see if someone else knows of a better solution before running the compile commands.

---

### Post by TiLaser on 2007-12-31
I solved the problem by reinstalling util-linux.  I downloaded util-linux_2.13-8ubuntu1_amd64.deb from [http://download.thaigrid.or.th/pub/ubuntu/archives/pool/main/u/util-linux/](http://download.thaigrid.or.th/pub/ubuntu/archives/pool/main/u/util-linux/) and moved it to /var/cache/apt/archive then ran sudo dpkg -i --force-all /var/cache/apt/archives/util-linux_2.13-8ubuntu1_amd64.deb and the problem is solved.

---

