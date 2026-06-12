---
title: "make: Nothing to be done for `all'"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by magicman5421 on 2008-04-13
ok so i'm trying to use Eclipse in ubuntu 7.10 and i keep getting the error "make: Nothing to be done for `all'". I wrote a very simple, standard "hello world" program (basically just cout<<"Hello World"<<endl;) and in the "console" window all I get is
```
**** Build of configuration Debug for project HelloWorld ****

make -k all 
make: Nothing to be done for `all'.
Build complete for project HelloWorld
```
What is going wrong?

---

### Post by ptn107 on 2008-04-13
Post the contents of the makefile.

---

### Post by magicman5421 on 2008-04-14
```
################################################################################
# Automatically-generated file. Do not edit!
################################################################################

-include ../makefile.init

RM := rm -rf

# All of the sources participating in the build are defined here
-include sources.mk
-include subdir.mk
-include HelloWorld/subdir.mk
-include objects.mk

ifneq ($(MAKECMDGOALS),clean)
ifneq ($(strip $(C++_DEPS)),)
-include $(C++_DEPS)
endif
ifneq ($(strip $(C_DEPS)),)
-include $(C_DEPS)
endif
ifneq ($(strip $(CC_DEPS)),)
-include $(CC_DEPS)
endif
ifneq ($(strip $(CPP_DEPS)),)
-include $(CPP_DEPS)
endif
ifneq ($(strip $(CXX_DEPS)),)
-include $(CXX_DEPS)
endif
ifneq ($(strip $(C_UPPER_DEPS)),)
-include $(C_UPPER_DEPS)
endif
endif

-include ../makefile.defs

# Add inputs and outputs from these tool invocations to the build variables 

# All Target
all: HelloWorld

# Tool invocations
HelloWorld: $(OBJS) $(USER_OBJS)
	@echo 'Building target: $@'
	@echo 'Invoking: GCC C++ Linker'
	g++  -o"HelloWorld" $(OBJS) $(USER_OBJS) $(LIBS)
	@echo 'Finished building target: $@'
	@echo ' '

# Other Targets
clean:
	-$(RM) $(OBJS)$(C++_DEPS)$(C_DEPS)$(CC_DEPS)$(CPP_DEPS)$(EXECUTABLES)$(CXX_DEPS)$(C_UPPER_DEPS) HelloWorld
	-@echo ' '

.PHONY: all clean dependents
.SECONDARY:

-include ../makefile.targets
```
I didn't write it myself obviously. If I start a managed make project I don't have to write a makefile do i?

P.S
I'm sorry if i'm being a huge noob, I'm used to micro$oft visual studio where you write your code and press go and it goes.

---

### Post by magicman5421 on 2008-04-14
bump

---

### Post by ptn107 on 2008-04-14
Did you try
```
make HelloWorld
```

---

