---
title: "ddrescue - checking for damaged files after rescuing"
date: 2011-10-14
forum: Any Other OS
---

### Post by bsilver6 on 2011-10-14
I've just had great success using [GNU ddrescue]("http://www.gnu.org/s/ddrescue/ddrescue.html") to rescue data from a faulty USB drive, leaving me with error blocks down to only a few kB worth.
I wanted to post a script I've written, based on the instructions in the [ddrescue manual]("http://www.gnu.org/s/ddrescue/manual/ddrescue_manual.html#Fill-Mode") for how to use ddrescue to search out and tell you which files have the faulty blocks in them.
I hope this is the right place to post this and hopefully someone wondering how to do this will find this post.

```
#!/bin/sh
# ddrescue-checkrescuedfiles

# Scans the results of a ddrescue rescue to find which files might be damaged
#  because of having bad-sector blocks in them which weren't able to be rescued.
# This script follows the algorithm described in the GNU ddrescue manual,
#  Section 8 "Fill Menu".
# http://www.gnu.org/s/ddrescue/manual/ddrescue_manual.html#Fill-Mode
# Note that the files which this script discovers as having bad-sectors will
#  in many cases still be perfectly usable, they may only have one or two bad
#  sectors in them. In the case of MP3s, JPGs, videos, etc, you may not even
#  notice. This script will just give you some information on which ones may
#  have errors in them.

# Before using this script, you must have rescued as much as you can using
#  ddrescue. Make sure when doing these initial run/s of ddrescue to use a log 
#  file and not to use sparse writes.

# This script needs to know the path to the device or image containing rescued
#  data (RESCUED_DEVICE), the path to the ddrescue log file (DDRESCUE_LOGFILE),
#  as well as the type of filesystem the rescued device was using.
# It also needs an empty directory to use as a mount point for the device/image
#  containing rescued data (completely arbitrary, just needs to exist and be
#  writable).
# These parameters must be set within this file, by editing
#  SCRIPT PARAMETERS, below.

# Example usage, rescue from /dev/sdb1 to ~/RESCUED_IMAGE:
# First rescue as much data from /dev/sdb1 as you can, using ddrescue:
# $ ddrescue -n /dev/sdb1 ~/RESCUED_IMAGE ~/DDRESCUE_LOGFILE
# $ ddrescue -d -r3 /dev/sdb1 ~/RESCUED_IMAGE ~/DDRESCUE_LOGFILE
# Then, edit this script to set RESCUED_DEVICE to "~/RESCUED_IMAGE"
#  and DDRESCUE_LOGFILE to "~/DDRESCUE_LOGFILE" (as well as setting correct
#  filesystem and mount point) and run the script.

# Results will be printed to stdout and will look like, e.g.
#  /path/to/file1: OK
#  /path/to/file2: FAILED
# Note that FAILED does not necessarily mean file is bad, it just means there
#  are some bad blocks in it. OK means that there are no faulty blocks in the
#  file.

# Results, as described above, will be output to stdout, while script status
#  messages and errors will be output on stderr.
# This means you can capture the results without the status messages and errors
# e.g. run 'ddrescue-checkrescuedfiles > output'
# and you will still see " * Mounting rescued filesystem..." messages, etc. on
# terminal, but "/path/to/file1: OK" results will go to a file called "output".

# SCRIPT PARAMETERS
# *** SET THESE! **************************************************************
FILESYSTEM="ext3" # Type of filesystem we are working with (for rescued medium)
RESCUED_DEVICE="/path/to/rescued-device" # Path to device or image
DDRESCUE_LOGFILE="/path/to/ddrescue-logfile" # Path to ddrescue log file
RESCUED_MOUNT_POINT="/mount/point" # Directory to mount device or image in
    # (must exist and be writable but could be anywhere)
#******************************************************************************

# Check script was run as root
test "`id -u`" != 0 && { echo "This script must be run as root" >&2; exit 1; }

# Arrange a temp dir to work in
# (filename is "<script base name><script PID>" plus optionally "-" and a number
    # if dir already exists)
TMPDIR="/tmp/`basename "$0"`$$"
TMPDIRBASE="$TMPDIR"; i=1
until test ! -e "$TMPDIR"; do TMPDIR="$TMPDIRBASE-$i"; i=`expr $i + 1`; done
mkdir "$TMPDIR"

# Mount rescued file system
echo " * Mounting rescued filesystem..." >&2
mount -t "$FILESYSTEM" "$RESCUED_DEVICE" "$RESCUED_MOUNT_POINT" || exit 2
echo "Done." >&2

# Recurse into rescued filesystem, building MD5 sum list, saving into temp dir
echo " * Building MD5 checksum list..." >&2
r () { for f in "$1"/*
    do if test -d "$f"
        then r "$f"
        else md5sum "$f"
    fi
    done
}; r "$RESCUED_MOUNT_POINT" > "$TMPDIR/rescued-md5sums"
echo "Done." >&2

# Unmount filesystem so ddrescue can work on the device/image
echo "Unmounting rescued filesystem..." >&2
umount "$RESCUED_DEVICE" || exit 2
echo "Done." >&2

# Fill the bad sector blocks with ASCII '1' (0x31) byte value
#  (this is an arbitrary, non-zero bytevalue and will cause md5sums of files
#  with bad-sector blocks to change)
echo " * Filling bad-sector blocks with non-zero bytevalue..." >&2
# Create a tmp file containing the arbitrary bytevalue for ddrescue to fill with
#  (ddrescue takes this filename as an argument when in "fill mode")
echo -n 1 > "$TMPDIR/bytevalue" || exit 3
ddrescue --fill=- "$TMPDIR/bytevalue" "$RESCUED_DEVICE" "$DDRESCUE_LOGFILE" 2>&1\
    || exit $?
echo "Done." >&2

# Re-mount rescued device/image
echo " * Mounting rescued filesystem once more..." >&2
mount -t "$FILESYSTEM" "$RESCUED_DEVICE" "$RESCUED_MOUNT_POINT" || exit 2
echo "Done."
# Verify checksums using file created before, saving results into tmpdir
echo " * Verifying checksums..." >&2
md5sum -c "$TMPDIR/rescued-md5sums" > "$TMPDIR/results" 2>&1
echo "Done." >&2
# Unmount rescued filesystem for the last time
echo " * Unmounting rescued filesystem..." >&2
umount "$RESCUED_DEVICE"
echo "Done." >&2
# Fill bad sectors with zero (0x00) bytevalue once more to restore image/device
echo " * Restoring bad-sector blocks to zero bytevalue..." >&2
printf \\000 > "$TMPDIR/bytevalue" || exit 3
ddrescue --fill=- "$TMPDIR/bytevalue" "$RESCUED_DEVICE" "$DDRESCUE_LOGFILE" 2>&1\
    || exit $?
echo "Done." >&2

# Print blank line and some text to stderr to make reading results easier
# NOTE: results can be captured from stdout, leaving stderr on display
echo >&2
echo "  RESULTS:" >&2
echo "(writing to stdout)" >&2
echo "----------" >&2
# Print results onto stdout
cat "$TMPDIR/results"
# Clean up temporary files
rm -rf "$TMPDIR"
```

Please feel free to modify/share/do what you like with this code.
Please do not run it unless you understand what it does. It shouldn't be hard to figure out if you read the [ddrescue manual]("http://www.gnu.org/s/ddrescue/manual/ddrescue_manual.html") and the [md5sum manual]("http://www.gnu.org/s/coreutils/manual/html_node/md5sum-invocation.html").

---

### Post by mips on 2011-10-15
Thanks, that could be useful in the future.

Just a though, determining the faulty files/sectors before running ddrescue would allow you to avoid the bad parts when running ddrescue and saving you lots of time.

---

