---
title: "Thunderbird Segmentation Fault"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by sleepytom on 2007-01-27
I'm having trouble running Thunderbird when users other than myself are signed in. When I start it for the first time, I can enter the configuration information, but then when it tries to run, it shuts itself down. Running it from a terminal reveals this error:

```
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131: 15337 Segmentation fault      "$prog" ${1+"$@"}
```

Here's what a portion of /usr/lib/mozilla-thunderbird/run-mozilla.sh looks like, starting with line 130:

```

moz_run_program()
{
	prog=$MOZ_PROGRAM
	##
	## Make sure the program is executable
	##
	if [ ! -x "$prog" ]
	then
		moz_bail "Cannot execute $prog."
	fi
	##
	## Use md5sum to crc a core file.  If md5sum is not found on the system,
	## then dont debug core files.
	##
	moz_test_binary /bin/type
	if [ $? -eq 1 ]
	then
		crc_prog=`type md5sum 2>/dev/null | awk '{print $3;}' 2>/dev/null | sed -e 's/\.$//'`
	else
		crc_prog=`which md5sum 2>/dev/null`
	fi
	if [ -x "$crc_prog" ]
	then
		DEBUG_CORE_FILES=1
	fi
	if [ "$DEBUG_CORE_FILES" ]
	then
		crc_old=
		if [ -f core ]
		then
			crc_old=`$crc_prog core | awk '{print $1;}' `
		fi
	fi
	##
	## Run the program
	##
	"$prog" ${1+"$@"}
	exitcode=$?
	if [ "$DEBUG_CORE_FILES" ]
	then
		if [ -f core ]
		then
			crc_new=`$crc_prog core | awk '{print $1;}' `
		fi
	fi
	if [ "$crc_old" != "$crc_new" ]
	then
		printf "\n\nOh no!  %s just dumped a core file.\n\n" $prog
		printf "Do you want to debug this ? "
		printf "You need a lot of memory for this, so watch out ? [y/n] "
		read ans
		if [ "$ans" = "y" ]
		then
			debugger=`moz_get_debugger`
			if [ -x "$debugger" ]
			then
				echo "$debugger $prog core"

				# See [http://www.mozilla.org/unix/debugging-faq.html](http://www.mozilla.org/unix/debugging-faq.html)
				# For why LD_BIND_NOW is needed
				LD_BIND_NOW=1; export LD_BIND_NOW

				$debugger "$prog" core
			else
				echo "Could not find a debugger on your system."
			fi
		fi
	fi
}
##########################################################################

```

I tried copying ~/.mozilla-thunderbird from my username into somebody else's username (and reassigning the ownership of the files), but that didn't help anything. I briefly see Thunderbird open and then immediately close just like before.

Any ideas?

---

