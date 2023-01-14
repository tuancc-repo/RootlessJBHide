# RootlessJBHide
 A Framework for Hide Rootless Jailbreak.

 It stores all jailbreak files in a random root directory, and splits the running APP into two worlds through a blacklist*, one of which is the jailbreak world that can access the jailbreak environment. The other is the original world that cannot access the jailbreak environments.

## Modules:

JBHide App: Provide UI interface for operating blacklist* to hide jailbreak, and UI interface for operating VarClean.

jb root path randomize: A set of libraries for generating and supporting jailbreak environments that stored in random paths.

tweak inject filter: A component that prevents injecting tweaks into apps in the blacklist*.

amfid bypass filter: A component that prevents bypassing signature checks for apps in the blacklist*. 

var clean: clean up files in /var/ those generated by leagcy jailbreak apps/tweaks.  

var redirect: A tweak used to redirect some related support files generated by the system for the jailbreak app to the root directory of the jailbreak.

## Features:

jailbreak undetectable when reboot device and jailbreak deactived.

jailbreak undetectable when put an APP into blacklist* of JBHide.

## Usage:

The tweak and app in the jailbreak world can obtain the path of the jb root directory through a special environment variable "JBRoot" .

examples of C/C++ code:
```
    char my_file_path[PATH_MAX]={0};
    snprintf(my_file_path, sizeof(my_file_path), "%s/my_file_path", getenv("JBRoot"));
```

examples of Objective-C code:
```
    NSString* my_file_path = [NSString stringWithFormat:@"%s/my_file_path", getenv("JBRoot")];
```

## Suggestion:

All jailbreak tweaks and jailbreak apps should not store any files in /var/. Instead, they should be stored in the app's sandbox container, or in the jailbreak root directory. Any files in /var/ files which generated by jailbreak tweak/app, will be easily detected by the "stat" API, and will be cleaned by VarClean in the future.
