# SyeOS (Systemic OS)
**Author: the same old Lion**

_Version: 4.5.5.2_

#### Introduction
Modern user interface systems are now targeted at giving programs full control over hardware and data, without asking where the data goes and why, despite having almost developed measures to intervene or limit scope of the access per application, and per process.
Furthermore, modern UI practices become a collection of archaic visual patterns to pose more distraction than usability, it made its roots so deep into general application architecture as everyone now discard Unix philosophy and tries to re-implement a wheel, because cross-integration is nowhere to bee seen in OS and FOSS philosophies.
SyeOS philosophy was thought after Portable Workstation requirements: virtual worskpaces, flexible action association, app sandboxing and one device multi-user support, suitable for Network Administation, Intellegence & Journalism, Investigative Scientific Analysis and Multiple Virtual Machine management.
The provided below philosophy must apply not only to the OS itself, but for applications written for it.
Diffrent philosophy points in paragraps are listed as PN, where P is short for Philosophy and N is a number.

## Philosophies and Concepts

### Apps

#### Data Scope

P1 An app should work only within its specified data scope, reducing scope of environments that already ARE or WILL be implemented by other applications and limiting its knowledge base to only what is necessary to operate, request and processing minimalism is the key to more managable apps.
P2 An app should not expect the ideal conditions to operate within, it must posess adaptive behavior to avoid unwanted ones, such as **[Streams and FileSystem isolation, P2]**
P3 An app must be ready to operate within different contextes (e.g limited data provision) ran in different instances
P4 One configuration directory for all apps
All apps settings should be stored in single directory with subdirectory of app or otherwise the access of one app to another app's settings should have strict data protection leveling and a system-managed permission (refer to AP in [Security] section), all of such settings must be available to edit from the settings system menu, all interconnected inherited settings should be unified, such as: keybindings for the same category of apps, thus way user will have unified control experience, it will work the same way in every app of the same type.

#### Functional and visual design

P1 Metafication - an app functionality must be a constructional part for package, its natural behavior must be close as to Framework-like activity in terms of programming: a single app is logic and activity in first place and only in second a unique design, if application is suitable for being used as a middle-man for other applications, it totally must - in order to reduce their unnecessary complexity, one of examples of such in regular OS will be FileSystem Dialogs - in this matter, they must be held by File Navigator, in the same topic - application must be as compatible with console or "direct" input just as with the visual UI, separating the functional logical part from visual server part (Metafied UI).
P2 Applications must use shared classes and abstractions whenever it is possible, to limit interface variability both for visual and programming experience and make everything fit together better - such concept as where to place tab and page visual control elements must be consistant from app to app, thereby Metafied UI is better method of achieving both flexible and uniform UX
P3 Metafied UI - for the application visual host, the visual appearance must be specified separately, in scripting matters (for example XML + json, HTML + json) and parsed by System Application for UI handling, stitching the logical and visual interfaces together.
Functionally similar workflow apps must use the same Metafied UI design  - with 0 deviations, thus using only 1 UI capsule for every of those is preferred.
Example: Telegram, Discord, Viber, WhatsApp, SnapChat, Facebook Messenger, Signal, Threema - can be grouped together into their own group, there is one optimal interface for "messenger" app, as the data and info flow is not flexible, unlike IDE that has specifics - one IDE for mobile apps, other for games, other for web apps & so on and so forth.

Visual interaction elements must have the same experience app-to-app.
Visual element disposition and visual obstructance must be NOT ADDICTIVE NOR ANNOYING, targeted at the fastest representative data perception and management as possible, such deviations as different button flavours, that essentialy do functionality that can be combined by action mix analysis into one button is not tolerated (refer to the video on Audacity re-desing and how they managed to make it more unified & concise - https://youtu.be/QYM3TWf\_G38 )

Every list of object, every textview must have a search functionality - for lists to select from them faster; for text fields - to find partial matches.

P4 Subvertial UI / Subverts:
In the furtherfy matter, contextual applications is a great addition to the OS UX architecture to make it more unified and less distractive, few of common OS practices can be unified under this category of applications and optimized by extracting their functionality into separate shared apps/libraries: text context menus, clipboard manager, search utility, IDE autocomplete proposal pop-ups, etc.
Subvertial, inter-inert, subline, inline functionality must be introduced too, in order to reduce visual obstructance (such philosophy is executed in IDEs which use context autocomplete popup instead of attached to the bottom of code editor - fixed autocomplete proposal frame)

P5 Metafied application hooks (Meta-libraries): such solutions as dgVoodoo, proven to be useful to make software with obsolete library dependencies runnable on modern hardware, but both dgVoodoo, game mods library hooks (Reshade) and other similars are in essence an adapting translation layer

P6 Plug-stack optimization behavior
If the condition is to be met with different outcomes based on previous conditions, app must have different methods in its logic to fire, changing the endpoint memory adress instead of deriving logic from accessing boolean, int or string variable - such practice should be placed before editing the pointer at which method should be called.
If the behavior is to be of a background or constant polling activity, but relies on conditional reasoning, it must have a pause/hibernation mechanism - the program must skip the code execution, when it is unnecessary, to limit the use of CPU/GPU cycles, same apply to information that goes to nowhere due to the final endpoint being unreachable - the suspension of the subroutine must occur, regardless to of which type the data stream is - strict data acess control described in [Security] sector provide enough of basis to solve such nuances as VNC software and online streaming [radio/audio/network server/etc]

P7 Contextual help and app's FAQ/Manual must operate with every user(operator)'s choice about data formats on basis of principle `describe Energy cost vs. Security cost`

#### Angelic Bus - event notification vs. polling
_**Angelic Bus is an OS Core Applciation and must reside within Top Execution Priority range (Time Critical?).**_

Data point optimization and event-driven formulation of states, sub-optimal and optimal derivatives in functional parts rather than idle - i'll call it Angelic approach instead of Daemonic, thus way such task as VLC media player or PipeWire will be required to notify the hibernation/sleep inhibition only once - and the subroutine for such, will be disabled - the reverting event may occur when PipeWire signals that the playback is entirely silent for N seconds (like 10+) or when app such as a PipeWire crashes or leaves the operational context - the state recalls to previous or otherwise logically-deriven new state: it is a more concise solution than diagnostical analysis of the information that is being determinanently generated inside the system,complexing the layer of unwanted abstraction loops. For every change of systemic [state], a stack of conditional judging must apply - such software as PiperWire might be not only one preventing the auto-hibernation timing, per se.
Such level of an API must be present not only in system services or system drivers, but also in every User Level Apps to further stabilize the system notoriety against stack overflows, unpredicted routine failures and such - app won't crash due to the driver crash in such philosophy, app will be notified of driver failure, leading to suspension or skipping of the activity (monitor disconnected -> media player pauses the playback).
Complex states like alarm clocks, planned events must be resolved through additional logic and timing event calling with stack awareness - if the events is not unique on the stack, or of repetetive type, it should be treated accordingly.
Angelic Bus (or rather Event Stack Service) logic:
Event - triggering point caused by specific system or application state, firing one or more listeners, if the event type is reaching of a specific date-time position or the event wasn't handled the precise moment it had fired, the CallOnMissRepeat logic will be used to determine the behavior
Listener - an entry in event listener's database, connecting specific event (System time/date change)
Listener.EndPoint - may be an adress of a process method PID:Method(), and adress of library method /library/path/sample/lib.so:Method(), anl shell command line/app calling "bash echo script", an path to write /dev/virtual/EthernetActivityLoss. Will be called when event occurs, passing either none of the arguments, or event data object
Listener.ReceivesDataObject (Boolean)
Listener.Repeat (Int) - how many times to repeat, if set to -1, then the event is 
Listener.InfRepeat (Boolean) - if true, Listener.Repeat will be ignored, and instead listener will be called every time Event occurs
Listener.CallOnMissRepeat = {None from past stack; One from past stack; Every from past stack}
Listener.CallOnMissRepeatOneTimeStackPos = MASK ({First, Last, Center, All})
Listener.DateTimeTolerance (Int)

##### Listener denial cases

For added or loaded:
Listener.Endpoint cannot point to NULL object;
If the .ReceivesDataObject set to True, the possibility of passing event call stack to the receiver target must be tested through AP/CCL list declarations check.

For added only:
Listener cannot have timestamp, that already have passed as its trigger.

#### Coding Logic Standards (CLS)
**Critical Reliance Mode(CRM) is a mode for executing vital applications, their code must be compliant with related CLS to sustain it.**

##### Basic

An application must be ready to work in "data flow" mode like a C/C++ object, where the real execution code of Object is separate from the Object Instance itself, and the Object Instance works like a data flowing into the optimized Object for RAM usage optimization and vice versa for Execution Time optimziation.
Dynamic programming techniques is highly advised, recursive is to be most avoided - stacking the calling stack every time will slow down performance by a lot, furthermore some of the loops can be executed simultaneously instead of one inside another.

C/C++ style case-switch jumps - compare first, then **jmp** to the **label** inside function scope, avoid using nested if-else statements.
Example:
```cpp
void execute_opcode(int opcode) {
    // Array of memory addresses for the labels
    static void *dispatch_table[] = { &&op_zero, &&op_one, &&op_two };
    
    // Jump directly to the memory address + offset
    goto *dispatch_table[opcode]; 

op_zero:
    // routine 0
    return;
op_one:
    // routine 1
    return;
op_two:
    // routine 2
    return;
}
```

Dynamic parametrical behavior instead of if-else in Time Critical Subroutines
Example on how-to
```cpp
#include <iostream>
#include <functional>

class Example {
public:
    void m1_active() { std::cout << "Scanning directories and re-establishing the lsiting list...\n"; }
    void m1_passive()  { std::cout << "Listing directories as FTP server...\n"; }
};

int main() {
    Example FTPServer;
    std::function<void()> stateAction;
    contentChanged boolean = False;

    // Conditionally assign the proper method (can be changed then even for multi-threading case independantly, if the variable is visible to the method which will change it!)
    if (contentChanged) {
        stateAction = [&FTPServer]() { FTPServer.m1_active(); };
    } else {
        stateAction = [&FTPServer]() { FTPServer.m1_passive(); };
    }
    
    stateAction(); // Just an example

    return 0;
}

```

Use array accessing or **jmp** instructions instead of switch-case when counted association needed, when it is faster
Example (in this example, it will work slower, but when working with wide range of possible numbers, it'll do)
```cpp
std::function<void()> mtds[2] = {[&FTPServer]() { FTPServer.m1_passive(); }, [&FTPServer]() { FTPServer.m1_active(); }};
//...
stateAction = mtds[(int)contentChanged];
```

**Never ever make a function (in low-level programming languages) which will do return values instead of outputing them into the variables**

Array Access optimization: Indirect Array Access for non-static Arrays
Indexes of the array must be stored as a separate, re-arrangable array, when the data containing part must be stored as bare, thus way, the program won't re-arrange the heavy data contained in the Array every time the sorting must change, the logic can also be used to acess Dictionary Arrays, where the string corresponds to the index in the Array.
Example:
```cpp
std::vector<MyHeavyObject> arrayData;
std::vector<size_t> indexArray;

// Initialize
indexArray.resize(arrayData.size());
std::iota(indexArray.begin(), indexArray.end(), 0); // Fills with 0, 1, 2...

// Sorting the index array (Data stays untouched)
std::sort(indexArray.begin(), indexArray.end(), [&](size_t a, size_t b) {
    return arrayData[a].someValue < arrayData[b].someValue;
});

// Accessing data in the sorted order
MyHeavyObject &result = arrayData[indexArray[requestedIndex]];
```

##### CRM: SyeCore

P1 The parts of the code must be separated into distinct categories by underlying result of malfunctioning:
Category 0: Malfunction yields 0 or insignificant amount of harm, or harm that can be corrected on the next execution cycle (looped processes, HW PID sensing, repeatable control surface cycles)
Category 1: Malfunction yields critical execution error, and program must be re-started -> restart routine must be called in such state, or specific SYS interrupt fired for such.
Category 2: Malfunction yields over-time accumulation of instability and errors -> monitoring procedures must be present, to detect and time the program re-run event when necessary or to filter the data provided (e.g erronous sensor reading; sensor reading that fall out of the data log, being a 1-time deviation, caused by hardware calculation mistakes, bad wire contact, etc)
Category 3: Malfunction yields critical operational error, that can be mitigated only by the operator input -> operator feedback algorithm must be present
Category 4: Malfunction causes subsystem or mission failure -> if possible, must be entirely avoided or code architecture must be re-thought

P2 Log slowdown
Dilemma on which logging operations should be processed immediately and reported immediately or which can be slowed down must be solved by the programmer(s) while writing the code, in order to free up the execution time for critical code execution.
If logging can be avoided without information loss, then it must.
If logging cannot be avoided due to it being a cause of information loss, then the logging priority must be introduced:
If the critical code part has a relief assigned times, the log scope must be accumulated within the application and be transfered only within this specific time.
If the parallel log reporting is possible, then the program should report logs in parallel, freeing up execution time fort the main code cycle, critical for the system stability.

P3 Pragmatic informational interrupts
Operator notification process MUST NOT interrupt the critical code execution.
Operator notification must be thought after the design of the operated system type, if it requires operator high attention span on multiple things or one dashboard requires multiple operators, the warning, cautions and logs must not interrupt the operatory process itself either, but point to mission critical information (if any)

##### CRM: Aerospace Cyclic Executive Architecture

P1 Time Partitioning:
Process/Container must receive a dedicated, strictly counted **Operational Time Window** in which 0 other processes can crawl (example: 40 ms every 100 ms)

P2 CCL Schedule Table
**CCL** calls must execute not by dynamic request, but by strict, assembled schedule. If the program asks hardware or other program to respond, the request got stored in a buffer and gets deployed only when the strictly assigned cycle tact arrives.

P3 Main+ISR Lockdown
Asyncrhonous interreptuions from the real software gets blocked(ignored) or isolated throught ***Angelic Bus**. Programs must relay only on static «state» snapshots

P4 Main+ISR Lockdown Buffer Overflow mitigation
To mitigate the Buffer must have unification (no two exact requests) and a request limit for Handle_ID

### Security
`General idea - compartmentalisation, one area of activity - one area for threat to spread, one area to lockdown after compromisation`

P1
ACL (Access Control List) and  AP (Access Policy) everywhere.
Every bit of information provide a potential **data point** for telemetry, PUPs and spyware potentially providing information to malicious actors.
Every access route provide a potential failure point and a potential vulnerable route for malicious actor's attack vector, so must be limited only to necessary software to operate with.

P2
App must not let User expose themselve to threat, if Application know that there is some door, it must not leave it unsupervised, only user/optimization setting can be taken as an excuse

P3
Every Application must be compliant at least with **CLS CRM: SyeCore** standard, so it can be switched or compiled into **CRM**, so the OS will be reliable enough to be used in Church Broadcast Media, Security Stations, Power Transformer Operator Consoles, etc.

#### Hardware Layer Encapsulation

##### ACL & AP

For every hardware component, a separate OS module must serve it as a **driver** and as an interaction service, isolating the system applications from direct access to the device's hardware without explicit Access Policy authorization.
Each and every hardware layer interaction must be tunneled through filter, limiting its abilities - even video graphic libraries must follow strict, defined rules and have Honeypot plugs where ACL specifies.

> Ref: Modern graphic cards can be flashed, over-clocked or damaged by other non-authorized means by calling specific sequences of commands. Such software as DeNuvo protection, reportedly, have succesflully damaged Nvidia RTX series graphics.

##### Treating HWID 

Identificating data outside of the System Core Applications undergo masking procedure, and for identifiers that must be exposed - variability:
HWIDs, device partnumbers, device names must be masked for Outside-Of-System-Core diagnostics, for example removable device HWIDs and drivers used must not be exposed to external software, instead it must be masked to "blank" or confusing data.
MAC adresses for networking hardware must mutate frequently to avoid SigInt procedures from external (non-on-the device) intellegence and confuse internal (on-device: apps) intellegence, if any is present.

Raw hardware data (streams) - visual, audio, etc -> Refer to further documentation, application isolation philosophy apply.

##### Hardware management security

Automated app execution and auto-play features tied to the hardware, must be not supplied with OS and warned about, when user tries to set-up such behaviors manually -> exposing any application to the data stream is vulnerable behavior, potentially opening backdoors for CVEs.
Changing hardware configuration settings must be limited by a time delay, making it is impossible for application if it somehow broke down the OS defenses, to mask the fact of readig hardware device's data stream by turning it off and on, when it is said to stay off (audio microphone/network device on-off fluctuating on OS control level)

#### Streams and FileSystem isolation

Data channels & hardware data streams must rout through Routing Channel Service(s): middle-man type services or libraries to adapt the resuilting data for underlying context or to limit its spread by providing AP limitations, in such essence all of the FileSystem operations must provide interface to be hooked  by System Level Applications.
P1, here - what the different apps see is not what under the hood.
P2 don't expect data traffic to match the logistics architecture just because of architecture's own integrity - calculation, user, logic errors will eventually happen [Murphy's law]:
General purpose data streams must be actively truncated/filtered down to expected data length and format, not behave with whatever data as granted - but to avoid, fix or discard any mutation and report to the System Event Log if any occur.

#### Access hierarchy

##### Application-based

System hardware and information access level hierarchy must not only be contained, but disjointed whenever it can be.

Hierarchical Access De-elevation (HAdE): acess privelegies to hardware spread downward from Core OS to system level applications (SLApps), to user level applications (ULApps) to lower-tier and midpoint applications, every level having less **acess rights**,, than previous - revoking access for application to certain HoDAP, revokles it also for apps, deriving their own access from that specific application. It may sound vulnerable when thought outside of the full picture, including only ULApps without SLApps and Core system - the point is not to make everything intertwined and dependant, the point is to make access hierarchy, dedicating the top access level to the most sturdy, unshakable parts of the architecture.
Android-style APs for applications and processes - route of accessing specific Hardware or Data Access Endpoint (HoDAP) creates Access Policy, if it doesn't have textual description filed to provide for user readibility, SLApps interfaces for AP control must provide plain text derivative to which application specific data route is attached and where, for **example**: 

`"Config.json" at HoDAP ~/etc/applications/SonyPictureview/settings/Config.json from package EntyCodecStudio.SonyCamerasUtilities.SonyPictureView
App own mountpoint: /cfg/Config.json
Broad Space Mountpoint: ~/etc/cfg/Config.json`
OR
`"Stream" at HoDAP "/dev/usb/S092-004928/Stream" from package EntyCodecStudio.SonyCamerasUtilities.Drivers.S092
Hardware Endpoint
HWID: [...]
Serial: [...]
Device Type: Camera
Device Description: Sony™ S092 Portable USB Camera`
OR
`Method "CaptureWindow()" at "/bin/lip/ScreenRecord.so"
Meta-lib config id: -1`

Same logic must apply not only to Applications, but to their Processes and thus, more restricted analog to "Execution Context" - an application, called from other application, may execute operations with data within the provided context, to prevent application behavior outside of the context, the Fiesystem File Access hierarchy will do, as it should be used to limit applications to not write or read from outside of the context, and thus to write or read data between the "contextes" if not granted to do so.
Applying ACLs for processes separately enables containerization and Virtual Workspace Isolation.
Creatinng new ACLs for libraries will create new meta-libraries for them, specific to application/process (so-called Meta-lib configs) - a library/linker headers/hooks to limit the execution scope by removing methods/variables to which access is restricted.

##### Process-based

An application, process may expose a fixed set of pointers to its methods calling adresses or to its variables, this set is called Calling Control List (CCL)
Such sets of on-fly calling must also have ACL and be strictly limited by the Sibliage level.

##### Sibliage:
**Application and Package based**
If the application is one providing the functionality through HoDAP, AP or CCL for the other, lower tier of privelegies application it is considered **Functionality Provider** [by ]{.underline} **AS**(App Sibliage)
FP by AS, which has rights over other application and is required to be ran first before the other application is running is considered **Parent** by AS.
Applications with Parent status is able to access the Children App's full CCL without explicit limitations to counted set of CCL elements.
**Parent** by AS can provide its ACL/AP traits to Children or limit them, when the parent application calls Children it can directly manage its RAM/VRAM without CCL wrapping.
**Relative** by AS apps can access each other's HoDAP(s), If the two Neighboring apps trying to access the same HoDAP without AP or Relative status, the access will be denied.
**Neighbour** by AS are applications that share the same Access Policies traits and Providers/Parents.

**Process based**
If the App Proccess is calling another Application to be instantiated as a new Process, it is a **Parent** process by **PS** (Process Sibliage)
If the App Process is the Process called into instantiation by other App Process, it is considred Children by PS.
Parents by PS can only use CCLs on Children application processes if they have their declared ACL permissions, otherwise they are forbidden to; They cannot use direct control of the RAM/VRAM of the children processes.
Parent by PS can specify the new process's start-up parameters, limit or expand the Children execution context (within its own eligibility spectre), provide to it HoDAP access and manage the Process's execution state (freeze/unfreeze/terminate, lower Time Priority).
Being Parent by PS absolutely does not equal to being Parent by AS, the caller application cannot fully manage the app called, instead it is just providing to it its own or even more limited execution context, it doesn't automatically grant permission to execute CCL calls, their list must be negotiated.
Neigbours by PS are processes called within the same execution context (container).
Neighbour and Children apps cannot execute CCL calls, exchange HoDAPs without explicit Acces Policies, declaring two apps to be eligible to be classified as a Relatives by PS grants them access to calling specified list of CCL calls.

_To handle the process finalization tree, the metafied framework apps are called from Metafied UI Provider Service (MUIPS) instance, positioning the process as a Children, to which the MUIPS has limited operational access, and thus can call events assigned to visual elements and metafied framework app should then be able to re-run and re-fill the instance of MUIPS if it crashed separately from the Children application, filling values in its visual elements where needed, this way the metafied framework type application shouldn't have excessive information about hardware rendering and HID._

###### CCL Isolation (VMM)

CCL functionality strictly must be isolated in its own containment (presumably, VMM subroutine/sub-service):
To prevent Return-Oriented Programming (ROP) attacks, memory corruption exploits, and reverse-engineering of memory mappings, no application or process is permitted to read raw virtual memory pointers or entry-point addresses of other processes or system meta-libraries via CCL tables without explicit Access Policy permission.

1. Shadow Call Handle Tables: VMM and the OS Loader intercept all dynamic link requests and compile a unique, isolated, read-only translation map for each container context. Instead of real memory addresses, applications receive abstract, rotated session tokens (e.g., Handle_ID: 0xAF31).
2. Late-Stage Runtime Routing: Real address binding occurs on-the-fly inside the kernel or VMM/VMM subsystem during execution. The process requests a call via Handle_ID, and the OS Core resolves and jumps to the obfuscated memory address without exposing it to the application's register visibility scope.
3. Vault Header Lockdown: Reading of dynamic headers and meta-library symbol layout tables inside the process space is strictly disallowed (PROT_READ is stripped from metadata spaces). Any unauthorized attempt to probe or scan memory for raw address disclosures (Address Leak Attempt) is reported to Overseer as Red/Black explicit malware activity, triggering Immediate Container Termination.

###### Pipelining and HoDAPs (VMM)
Hardware or Device Access Endpoints is a RAM Descriptor (Pointer), pointing to a data (variable or constant buffer, method/function, object, etc) wrapped by VMM.

distinct Pointer forwarding modes for each and any Wrapped Pointer(HoDAP):
1. Constant:
Pointer to a protected memory space, for example `const char*` or `const uint64_t*`, wrapped by VMM and protected by it with flag `PROT_READ`.
When used: static data transmission (launch arguments, fixed object or file list, configuration parameter, meta-tag name, meta-tag metadata, file hash, etc)

2. Variable:
Pointer to assigned shared memory buffer fragment provided by VMM, limited by `Buffer Request Limit`, owner of the Pointer writes to it, while target user of the Pointer can only read it.
When used: dynamic data (pipelining, network buffer, FileSystem stream, transit video frame)

3. Method (Shadow CCL Handle):
Handle_ID index in Shadow CCL Table is passed, upon calling OS translates the masked method call token into real adress and calls it.
When used: signaling, event notification, complex application logical intertwining (meta-apps, libraries, meta-libraries, etc)

4. Class instance (Proxy Interface Table routing):
The object persists within the Dedicated Kernel Pool or within the Owner Process memory, the target user of the Pointer receives new Shadow CCL Table Handle_ID for the Proxy Interface Table, routing the object's fields as either Constant, Variable or Method through previously mentioned VMM routing processes.\

For the Unwrapped Pointer(HoDAP):
**VMM** maps **HoDAP** from its memory segment onto both applications simultaneously.
For the ROP-exploit and unpermitted memory scanning, method adresses inside **vtable** must undergo **Late-Stage Runtime Routing**

Wrapped Pointers is used when the Owner and Target User applications does not have **Relative** status
Unwrapped Pointers is used when Applications have **Relative** status.

##### User-based: Common Interface Separate User Mode (CISUM)
At a permission, multiple users can use the same Workspace and same WorkScreen, associating each user to separate HIDs, giving a separate HID session to each / or by a separate VNC client account.
When working in separate screen sessions (separate physical or virtual(VNC) Displays), control elements available only at a previlege, can be displayed for the user that have them, separate from the user who does not, but when working on the same Physical Display it is not possible, so the users must choose.
Another matter is keeping track of CPPS and user-specific sensitive data propagation: the passwords, sensitive data must not be available, nor shared in Shared Workspace(s).
Every HID action in such mode must be routed through Angelic Bus with the UID (User ID) layer (based on HID/VNC client id), limiting the execution of the request for users that are not eligible.

Distinct methods to work with Privelegies Mismatch (users may choose one):
1. Lower the authority level - privelegies level will be capped at the level of the lowest Workspace member.
2. Draw adaptively for separate Screen/VNC sessions.
3. Adaptive action, unified display - every user will see other user's action, but only user with higher privelegies can execute the actions that do require such level, the control elements will be visible to lower-tier users, but will yield Unathorized Access error or be just unresponsive.

Connection management logic:
To estable the connection, agreement between users is required, but to close, command from any of the users will suit:
1. if the user is at lower tier, the connection will be closed for the user only
2. If the user is at higher tier and the hardware running the Workspace is functioning as the Mainframe (the user with the higher privelegies level is not local too), then the action selected by the System Administartor will be executed
3. If the user is the host, then the connection will be closed.

#### HWID filter services: hardware capabilities masking

A set of user-controlled options per Workspace/Application/Process

Keyboard filter option to change the typing speed and error count (the typed key sequence will be recorded and routed, when possible, on-fly or after the record)
Keyboard layout masking (to hide the count of keys available)
Mouse filter option to mimic different mouse DPI, response rates and user-specific navigation patterns (navigation patterns for touchpad and physical mouse differ, touchpad has more stutters).
Video stream masking through drawing applications with another bit depth, color pallete or resolution configuration and then upscaling/downscaling if needed. 
CPU/GPU cycle skip (pause) specific to app context - to imitate different clock speed, skip/pause application execution for configured N of cycles/for targeted clock rate.
Timezone and time error masking - assigning to a container a different (presented to it) timezone or even a clock error (adrift from the real UTC time):
Three distinct approaches could be used:
1. **CLS CRM: Aerospace Cyclic Executive Architecture**, P3:
  Isolated process/container is executed in this environment to prevent its logic of detecting isolation by analysis of asynchronous Memory Bus delays. 
2. **CSAC** simulation
   **CSAC** unit driver will be replaced with specific counterfit for simulating the timing intervals, cutting down or expanding **timestamp** when needed.
3. **CPPS** altered version
   **CPPS** will be replaced with slightly altered version to edit the chained time event sequences and provide virtualized **CSAC** information
To note, any of those must be used in parallel with FSOS replacement masking techniques.

#### Crypto and passkeys

##### FileSystem hash integrity

FSOS must strip away the file's metadata on write to drive, and then perform the hashing function on its raw content to then write the hash to the FileSystem-level metadata appointed to the file.
The metadata to be stripped is not a FileSystem-level metadata, but a file's own metadata, baked into its content.
Then, on the access to the file, if the file's content is mismatched with what FSOS/FileSystem remembers last about it, it must trigger a System Pause-Warning event, displaying the warning to the user to decide either to proceed with file inside Overseer, proceed with provisioning file directly or to decline it entirely (e.g routing the file to the application)

##### Separate machine and user passkeys

Machine settings, and topmost administrative settings must be managed through the separate password than the user settings and user applications settings

##### Compilers lockdown

Only local FileSystem interactions are permited for compiles to perform during the compilation, if downloading of some content is required, then it must be performed BEFORE the compilation software will involve.
Hybrid Overseer scanning (source and binary) is required after the compilation.

##### Binaries lockdown

When the system is started up, it must lock down at least its own Core Applications and Systen Level Applications, to be read-only [to avoid hijacking and malification even if the attacker gained acces to the write privelegies and somewhere they were exposed].
On the other half, the source code of every application must be stored in a package store and must be available for redaction, but thus way that both Core Application and System Level Application editing will require the Machine Settings Administrative authorization.
If user requires, then compilation process will be performed, the resulting binaries then will be updated on the next system start-up/reboot.
User-Level Application modification during the user session, on the other hand, won't be locked down by default, but it must be provided to user as machine-wide or/and user-wide setting, the machine-wide setting will act as a HAdE.

##### Bootloader timestamp protection

Proper timestamping with unchangable CSAC (Chip Scale Atomic Clock) is highly advised.
Every hibernation, boot-up, restart and shutdown attempt must be timestamped with the current system clock and logged for some time in memory readable only by the OS Core [encrypted with autogenerated passkey].
Then, to prevent "time-dillation" cryptography attacks, the OS must reject attemp to boot-up if the system time is lower or exact to the latest logged event.

##### Bootloader encryption with TPM/Hand-Held or Built-in Cryptvault

Advised: buil-in cryptvault activable only by biometric identification
Less advised, but ok: TPM/plugged-in Hand-Held cryptvault
Supported, but not advised: manually entering passkey string
Supported, but not advised: no encryption
Bootloader can be configured in a way, that it will be encrypted with the unique passkey, provided by the encryption module or the user, so the bootloader will be decrypted during the system start-up/wake-up process.

##### Cryptvault Password Provider Service (CPPS)
_**Core OS Application**_

In order to limit vulnerability of Cryptvault Devices, the OS's own service must isolate the device to itself exclusively during the OS shell runtime, providing cryptvault keys or cryptvault-encrypted/decrypted data to a specific HoDAPs [such Endpoints can be anything, files, strings, DB entries, device data streams, contacts, etc, ...] upon request.
For this matter,  decrypted data must never ever enter the persistent memory, only encrypted data is granted to reside within it, unrelated to which device performs the encryption/decryptiion routine.

_Suggested Cryptvault Device: YubiKey_

Request acception or decline must be determined through administrative level configuration setting per HoDAP, specifying if the biometric/password check is needed before proceeding, and to which ID the passkey[or passwordkey-based decryption/encryption action] pairs  (**Session Secrets**) it will point - for example, such practices of one target multiple pointers could be used to hook up the HoDAPs aimed at the specific contact in various messenger applications, to automatically encrypt content exchanged between the _contact_ and the user.
For the sake of the timestamped encryption the Cryptvault Password Provider Service must be able to perform timestamp-mutated key (TOTP) encryption, both for situations when the Cryptvault device is supporting it natively, and for situations when the Cryptvault Password Provider Service will perform it itself.
As an option, CSAC support and time latency tolerance settings must be present.

Session Secret Acquire:
User or OS may trigger a creation of new Session Key, either Cryptvault Device driven, randomly generated, or entered by the user's hand in combination or without a TOTP functionality.

Transient Session Secrets:
Cryptvault Password Provider Service must provide a channel to activate/deactivate presence of the specific Seccion Secret in the system, so the OS or the user can determine at which given moment, the Session Secret will be active or not, in which given execution context or at which given time of the clock. For the time-based Session Secret disabling, Cryptvault Password Provider Service must use Angelic Event Bus.

Cryptography Execution Isolation
All of the encoding and decoding routines must be witheld inside the CPPS subroutine, avoiding misconception where the 2nd or 3rd party application will execute the encryption/decryption routines and TOTP calculation, this is limited to only inside-OS routines and cannot be scaled for something outside of regular OS activities (SSL cryptography can be embedded in CPPS too) such as login credentials;
However modern era TOTP with Obstructography and Quantum-computing-safe cryptnet practices enables p2p5 and other peer-to-peer logic, that can be executed even on the regular network websites, entirely avoiding the problem of 3rd party application cryptography.

Anti-Radiation (Meltdown CVE mitigation)
If setting enabled, then **SYS_FLUSH_CRYPTO** command must be sent whenever the CPPS leaves the CPU control, to erase the possible remains of Secrets inside disputable CPU cache.
It MUST NOT be executed under ongoing active use condition, for example if the decryption/encryption process has not yet finished executing, but it can be executed if the user credential type of data is being asked for and has not been transfered yet (application which requested must handle this condition on its own, with just report from CPPS that request time has ended).
The **SYS_FLUSH_CRYPTO** condition must also block any new key generation or descriptor provisioning.

Applications auto-provisioned TOTPs:
For every app, if it is non-visual, an internal TOTP must be provided if the app doesn't state otherwise - it will be utilized for signing and app internal functionality.
For every visual application or Metafied UI-framework app pair, an external TOTP (readable by user) is required, if the OS config doesn't state otherwise (ref: **Window Manager Aura**)

Cryptsign procedure (for Applications and Users-UIDs):
Cryptsign key is **Ed25519** or **ECDSA** internal created and stored in CPPS Vault per Application or User.
When the application calls CPPS.Sign, the method will use information who the caller (application) is to retrieve the related key and sign the provided binary data with it.

Tip: such logic must as well be used to encrypt specific data partitions on drives or folders, to decrypt it only before the data is provided to the proper application assigned by the FSOS.
For the matter, if the operation is to be performed for the file, a metadata stripping for file hashing must be performed by FSOS or its respective module.

By all means, the exposed by the Cryptvault Password Provider Service routines and signals are a valid entries for AP regulations, so no explicit statement about security at this level is required, as **by default the HoDAP access must be authorized**.

##### Password Manager Service (Keyring Service)
_**SLApp**_

Password Manager must store the data encrypted by the Cryptvault Password Provider Service and behave mimicking it, providing a management service for passwords, that are known to user and can be changed by user, for example website credentials.
Despite being resemblant of the Cryptvault Password Provider Service, the Password Manager must be managed by the user level of the privelegies, and posses a default functionality like the password DB export (witout the encryption key to the passwords themselves included in it, it will still be encrypted), password generation if needed and such.

##### Obstructography

All cryptography functions must work in ct-time mode (Constant Time of Execution), where only the content encryption/decryption length influences execution time (as in LibSSL standards)
if the direct ct-time function code is impossible to implement, a delay functions must be used to burn up CPU cycles to make the function always execute within the same cycle count, a mix of both is suggested if the passkey and data has known maximum length to supress even intelligence analysis about how many characters the passkey or the data consist of.

When the encrypted data contains strictly structured information, with set array of variety of characters, then deadweight noise characters must be introduced before encryption and removed after, random characters in random places - such as in Lion's p2p5 concept, global software update hash list(list of hashes with hash per user) must be distributed (TOTP + both points of obstructography)

#### Application Heuristical Isolation Tool: Containers and VMs
_**Application Heuristic Isolation Tool is a System Level Application (not the OS Core Application from which the whole functionality of the OS stems, but a vital part that must be protected and do not fall into the category of User Level Applications)**_

Container [Configuration Logic:Containers] isolation is done through launching instance of the application inside an isolated Workspace context to limit its environment to virtually "clean" instance of the SyeOS without user data inside, it is done through plugging the HoDAPs and through providing Honeypot counterfeit HoDAPs; HWID Filter services are ran to imitate different running conditions and mask real HW IDs.
**Workspace Container Environment** - plug type of Honeypot HoDAPs establish, any non-permitted interaction will be reported to callee service (Overseer for example), application operates within the global VMM context.
**System Level Container Environment** - Hardware will be replaced with MITM type of HoDAP Honeypot, any call to real hardware will be imitated inside RAM or routed with fixed directives, leaving the spot for the permitted connections but logging everything, previous level of isolation (Workspace Level Isolation) practices also apply, but not only the SLApps are duplicatedly ran inside the isolated context, but a conterfeit System Service (OS Core Applications) such as VMM, FSOS & etc are ran to replace the real ones inside the containered environment to prevent any possibility on the middle-to-top level of security or behavioral issue.
**Virtual Machine Environment** - isolating and application inside a copy of the SyeOS, ran properly inside a Virtuial Machine Environment, applications emulate CPU and other hardware execution instructions of the SyeOS itself and the application tested.

For isolating app from global VMM context inside the Container-type of isolation and to exchange applications/files both inside Virtual Machine and Container isolated Environments, a separate, altered versions of VMM and FSOS are required: VMM must work with isolated VMM space as a real memory space, making all metrics convincing for contained application, that it is indeed, working with real VMM, which operate not within another VMM, but within usual SyeOS instance; for the FSOS, it must report the hash of the exchanged files as the hash of original ones, and if the application is to request altered SLApp or Core Application binary/library, the _special_ version of FSOS will provide the byte-to-byde content of the original files content to those apps instead, while the version working in the RAM is the altered one.

Four distinct states of Environment must be ran to analyze the hardware sniffing event(s) and detect detergent patterns:
1. Hardware unavailable - hardware device is rendered as non-present in the computer system.
2. Hardware is unuseful - hardware data stream is present as unuseful (for network hardware: no internet connection; bluetooth: no bluetooth devices found around; camera: white noise and black picture conditions; microphone: white noise condition; etc)
3. Hardware is providing unreal data feed (network: pseudo-internet mimicry, as in Malware Analyst Virtual Environments; camera: fake, pre-recorded live feed with random noise patterns atop; bluetooth sees and can connect/inspect a changing by time intervals set of imitated bluetooth devices; etc;)
4. Hardware is providing limited access to real data, isolated by a white and black lists

In VME (Virtual Machine Environment) it is feasible to also test the app's reaction to ACL change/widening, how the app will behave if it will be granted with higher permission level or count, that usually - user error exploitation testing.

Such practice of multi-condition testing may apply to any level of Isolation environment, from highest tier of VME downto Workspace Container Environment.
Additional test step with erasing and not erasing application cache (if any written) may be triggered (if non-manual mode - automatically, if manual - by user request).

The A.H.I.T tool must support three distinct operating modes:
Automatic testing (running the behavioral test pre-recorded before or pre-compiled )
Manual testing (running the A.H.I.T orchestrated by user)
Regular Isolation - used for Workspace running or behavioral test recording.

#### Overseer (Program Behavior Heuristic Scanner)
**Overseer purpose is to run apps inside A.H.I.T environments and analyze their behavior both for hehavior analytics metric, performance metric and threat analysis. It is an SLApp**

Deviations from declared ACLs will be considered a malware threat.
Deviations from data security protocol ideology of SyeOS will be considered a spy threat.
Deviations from declared APIs will be considred as a performance issue.

Overseer uses A.H.I.T, app productivity analysis (thermodynamic behavior, load bringed upon different parts of the system, execution speed) to detect if the application misbehaves, escalates, exploits or shares what it shouldn't;
Using thermodynamicity analysis on application while keeping score of which events and conditions happened will disclose the behavioral connections - if application is not an AI camera overlay tool, but it behaves differently when the raw camera feed changes, disproportionally to the information's binary data weight shift, most likely it is doing something wrong with the data. Same pattern applies to lower complexity data variations;
Honeypot-caught content will be tested against A.H.I.T environment's list of unwanted to transfer data, from high risk like system internals, passwords which shouldn't have been exposed to application by any means to more subtle, telemetric exposure or transmission about content which is private but within the application's visibility scope, down all the way to the content that is not considered private, but has 0 reasons to go online or inside any unathorized channel.
If the application misbehaves with access to data, to which it shouldn't have access to in normal circumstances, but were given for exploitation analysis, and despite seemingly no use to it, uses or shares - it will be flagged too.
For the app stability and vulnerability testing, the application will also be supplied with faulty, out-of-the-structure data (data, that has non-suitable structure, characters out of expected scope, noise) to detect probable instability cause and vulnerabilities (if any) - but, the type of data noise will remain the same, Overseer is not required to perform NSA level of JohnTheRipper alike scanning, instead for data exposure scanning Overseer will log how the application behaves if it knows when the sensitive are being entered or what it does with the data, that may be sensitive (fake passwords or password:account pairs, fake sensitive messages provided to it, etc).
As a matter of pre-caution and deeper approach, the Overseer tool will also refer to local heuristic and signature database.
Overseer must also cross-reference the application's visual style and visual layout (or Metafied UI file associated), to not mimic the System Level Applications, if the file is not from within it, the two distinct method dependant on either the application built in framework architecture style and uses Metafied UI or built as archaic style and uses own Visual Library must be used:
Metafied UI analysis is straightforward block-to-block analysis, with color approximation (close to each other colors will be considered as the same color - if the app mimics, for example, Password Manager for fraudstery reasons, users much likely won't notice a subtle palette difference, but the general design layout and elements), however imitation of non-critical SLApps, such as File Navigator, Web Browser, Layout Editor or etc. is not prohibited, since users may need their own flavours or realizations of such applications.
For the non-Metafied apps Overseer must use PDQ-alike techniques and color averaging.
Metafied apps and apps with proper CCL headers is the best for testing, since they can be tested through CCL calls.
For CCL calls from Overseer and for CCL calls monitoring by Overseer, it must have AP permission to skip CCL Isolation.
If the app exceeds the Buffer Request Limit under **CLS CRM: Aerospace Cyclic Executive Architecture** OS operating condition, it must be flagged as unoptimized or suspicious and its Execution Priority (for example, Time Critical) must be de-elevated by the Overseer, if the app itself is not of a high criticality (ref: **CLS CRM: Aerospace Cyclic Executive Architecture**, P4)

Overseer could be used to run not only unknown software, but also an unknown files inside known software to limit the threat possibility (if CVE is found to take effect when the file's inner structure is altered)
On the finish of the execution, Overseer will file a report about the program's behavior and related metrics, reporting to user vulnerability/threat level and performance scores during the security analysis pass, if the app scores enough credibility to undergo next pass (with lower tier safety in A.H.I.T) it will undergo automatically, if the application is not yet considered a threat, but misbehaves, user will be presented with option to stop on the current step or go further.

##### Configurability

Which is configurable, Overseer need to present an option to be disconnected from internet or to only pull heuristics databases from it, but never report to it.
Report to online user-induced database will be selectable from: All, Software Only, Threats Only, Software Threats Only.
Selecting "all" may expose the user's privately handled files, so the default setting is Software Only (the hash of the tested file wouldn't be present, neither the file ran inside software)

##### Threat categorization

###### Colors
Green - harmless legitimate software
Orange - suspicious behavioral drift
Red - explicit malware behavior, which can be contained through ongoing Security Protocols or through configurational hardening
Black - cannot be contained through current security practices of SyeOS

###### Shapes
Checkmark - everything is good
CheckerBoard - faulty software, that has instabilities or plainmode crashes due to data, condition variation or a run time (memory leak/subtle behavioral drift/slow but sure buffer or cache overflow/precision drift over time/sudden crashes or behavior changes and other minor instabilities)

Cross - data breach / spyware mechanics, intelligence and telemetry
Triangle - obstructware, fraudware and ransomware (non-harmful directly) - ad-inducing soft, crypto mining soft, etc
Square - destructive mechanics such as cryptsomeware, StuxNet, etc. - diversion targetted or unintentially hardware harming software
Circle - intrusion software, RCE, botnets, etc.

**Shapes can be combined together to mark multiple threat issues:**
Triangle with cross inside

Square with cross/triangle inside
Square made out of triangles, connected into a cross

Circle with square/triangle/cross inside
Circle with triangle, inside which a cross
Circle with square, inside which cross/triangle
Circle with square inside, made out of triangles and forming a cross

#### Overseer Critical Performance Scorer Module (source-code and execution analyst)
##### Suspicious characters counter
Source Code analysis

Scans for zero-width, escape, control and highly-weighted characters inside the Source Code, which are not a part of the regular set for programming in the Source Code language.

##### OnDe Score
Source Code analysis 

Ontological Density Scorer measures methods call graph complexity and API semantical cleanliness comparing the two to the overall Source Code byte weight (without measuring the weight of commented section)

##### API mutation score
Source Code analysis

If Overseer has test files for prevision version of the applciation source code, it tests the difference between declarations and header files, outlining the differences for the report of incompatible or extended parameters between the versions.

##### Documentation reliability
Source FIles general analysis

Matches the patterns of the provided API (headers) with the mentions provided within the allocated documentation for the program, if there are differences between them - warns about documentation deprecation state.

##### CCL table reliability
Source FIles general analysis

If the application's CCL table is incompatible with the real declarations of methods/variables within it, then Overseer reports fatal mismatch and stops before further analysis.

##### Codebase Compliance Score
Source Code analysis

Score is measured by the related count of total methods to the count of methods which have ftechniques stated as unwanted or forbidden in **CLS Basic** guidelines.
CLS compliance is measured afterwards, by checking source code against list of {forbidden, unwanted, proper} coding techniques, applications with insufficient score will be marked as unsuitable to be used as Core OS (incompliance with any of CLS CRM) or SL App (uncompliant with CLS Basic).

##### Thermodynamic Efficacy Coefficient score
Run-time analysis

Safety scan
If the program Thermodynamical Activity (CPU/GPU load) is way too dependant on the HoDAP inbound traffic content, the analyser lowers the application secureness score, as it has some inefficiencies or hidden stenographics. The measurement will be taken on the average when the different test data pattern will be applied.

Performance scan
The dynamic TEC measurement will be used to monitor quantity of activity spikes (TEC fluctuational fade/stabilization/spike) during execution of complicated mathematical operations will be added to OnDe analysis score.

If the Application is not a new version of Core OS or SL App and has higher OnDe score than that of an average for previous OS Core scores, the app will trigger warning flagging the coding techniques as unusually sophisticated (high optimization is not always a sign of malware, but user input will be required to clarify the situation)

#### Overseer Real-Time Protection module
_**Core OS App**_

##### Access List violation reporting
VMM, FSOS, meta-lib & other OS services provide reports to Overseer every time an application process tries to call CCL or HoDAP it doesn't has permission to.
If it includes a highly specific CCL/AP, the app doesn't even should have knowledge about, the suspicion level is being considered closer to malware, rather than poorly configured app or unstable application.

##### Real-Time Resource Usage Monitoring
Processes' resource usage are being reported to Overseer, if some process overuses the resources, despite the program common life cycle doesn't involve high computing demand, it will start analysis by Overseer suite.

##### Real-Time Execution Error Monitoring
If the process calls library/application method with triggering error/warning, it gets flagged as unstable.
If the process unexpectedly freezes or crashes (terminates prematurely without proper exit status report), it gets flagged as unstable application;

##### Note
_Connected to all of the monitoring events, Overseer keep track on the execution context, connecting the dots between other behavioral reports of the application (if it only nehaves suspicious under certain conditions, the conditions must be taken as the highest consideration about suspicious activities)._

##### Gatekeeper sub-module
Data Leak Prevention subroutine, can be configured to work in both, either of the three protection modes or even entirely turned off.

Sensitive data can be specified to Gatekeeper module in order to prevent the leak by actively detecting it in the traffic, such data will be monitored to not go to certain locations, dividing functionality of Gatekeeper into two separate categories.
Data can be specified from: Password Manager (by explicitly granting Overseer the raw information about the password, so it will be encrypted only by the Overseer's own internal TOTP and stored in Overseer's userdata...), FileSystem (the file can be marked as sensitive), manually adding string to the DB.

Categories of protection
**Active Raw Binary Scanning**
Networking services, clipboard service and keyboard filter service will report to Overseer its raw, unencrypted content and FSOS - raw only if the file is not ment to be encrypted, if the file's or packet body cannot be mistaken for binary noise inside a vast data stream (large compressed/encrypted data, media streams, etc) and plainly look like a DB/Structured Data (JSON, XML, etc) or plain text, the sensitive data fragment will be removed from the data and Overseer will be triggered to alert the user about Data Breach/warn user about reckless data sharing (if the action stems from user).

**Heuristical scanning**
1. Unified Input Stream Interception:
 Gatekeeper cross-references the outbound payload with metadata supplied directly by FSOS and CPPS on-the-fly. real-time verification include:
 A) In-Flight Content Hash Verification: FSOS reports the clean, stripped content hash of any data being buffered for transmission. If this hash matches a restricted file, system internal dump, or isolated application dependency, the transmission is halted.
 B) Transient Secret Sniffing Prevention: Gatekeeper pulls active Transient Session Secrets structures from CPPS memory. Any occurrence of raw passwords, active tokens, or cryptographic remnants within the network or bluetooth frame buffers triggers immediate isolation.
 C) Semantic Tag Matching: Ext5FSD passes attribute tags and "paperclips" associated with the source container context. Files labeled with high-security classification or contextual isolation markers cannot be exposed to outbound connections.

2. Behavioral Drift and Steganography Detection:
 Gatekeeper works in close synergy with the Overseer Critical Performance Scorer Module. If a process attempts to transfer low-complexity, static data streams (e.g., a blank image or steady audio feed), but the dynamic TEC score shows anomalous CPU/GPU cycles consumption during packet assembly, Gatekeeper flags the operation as Steganographic Leak Attempt (Shape: Cross / Color: Red), terminating the operational context immediately.
 Uniformely, if TEC of network interface(s) for the process is abnormally high, Gatekeeper must freeze the process upon investigating before un-freezing it and releasing from the active monitoring process if the traffic doesn't contain sensitive data and meet the expectations from the application (parallel Obstructography to Steganography detection).
 
3. Network Gateway Shutdown:
 Upon detecting a critical violation, Gatekeeper fires an immediate top-priority interrupt via Angelic Bus (SYS_FLUSH_CRYPTO), commands Overseer to execute Immediate Container Termination for the offending Handle_ID, and temporarily plugs the communication interface driver to ensure zero packet escape before the operator reacts.

**UnEncrypted remote FileSystem forbiddance**
When enabled, any attempt to transfer to any of the **communication interface**, [file]{.underline}, [directory]{.underline} or [inode]{.underline} will be prohibited by Overseer's response to FSOS analytics.
The interface will be temporarily plugged (closed) and the transfer operation inside FSOS will be terminated.
User will be notified about this event, proposing to specify or generate a TOTP or regular Passkey for the communication interface's location (Cloud Storage, FTP server, etc.)

#### System's Operator and User security
P1 Warnings and cautions about hardware, malware, operational, runtime environment threats and errors must not have option to "skip by default", even if they are recurring
P2 Informing techniques must be concise in order to inform fast
P3 Information techniques shall use combinatory logic for critical environments in which multiple warnings/errors/cautions can hit at the same exact moment. Ssuch as using combinatory logic for reporting (ref: example: **Overseer**, **threat categorization**) - it may use combinatory set of shapes, colors, sounds that do not highly interfere with each other and can be recognized under urgent information provisioning.

##### Window Manager Aura
To counter visual interface spoofing, a WM visual trait is required: Aura
Functionality: every appliaction will have colored shadow and/or symbolizing icon on its frame border.
The color of the shadow and the content of the icon will vary from app-to-app, and must derive from app's external TOTP, so it can be checked by calculator which application activity user is seeing.
Windows of the same app share the same Aura.
The effect is displayed as animated semi-transparent colored shadow/outline of the Window, the ongoing sequence is derived from TOTP and so is changing every time CPPS update TOTP.

**Theoretical screen capture mitigation:**
Provide screen buffer with no "Aura" effect present - exclude the content from screen capture pipelines.
(configurable: on/off)

##### Window Manager Overseer Bridge
Provide Overseer with HoDAP/CCL to make WM flag application/window acting unusually, by drawing on its border shape(s) in color(s) according to Overseer **Threat categorization**

#### Direct Hardware Contact isolation practice

##### General driver isolation practice

If the driver required to work with bare hardware level and perform afterward some logic, one layer of the application or one sub-application must do the heavy lifting and filtering in the part of the interacting with raw hardware, and the other part of the application/driver must handle the logical conversions, management and orchestration.

##### Limit the scope and authority of removable devices

Sessions of acessing the removable devices must be run inside a separate containment - one or another level of hardened execution context or even container environments [refer to A.H.I.T practice on container environments]

User must be warned when using media with volatile FS, such that can be used to execute code or can be damaged through operational halt, such FS must not be supported to format media into:
exFAT, FAT4

##### Workspace and Virtual Machine HID capture

If needed to avoid detection of slipping through information by exposing that certain key combinations do not ever execute within the Workspace or Virtual Machine, giving potential or hypothetical spyware a data reference, an alternative than a sequence to escape the encapsulation HID capture must be provided by SyeOS - a hook to respond on the pressing of power/reset button (not the event of lid closing for notebooks! important to not mix those up) - when the power button while inside an Workspace with active HID isolation (and there are no multiple HIDs, for example, keyboards/touchscreens to be associated with multiple screens), the SyeOS should just switch control back to the main host OS.
Configuration entries for Workstations with HID isolation: 
ReturnToHostESbyPowerButton (Boolean)
SendToIsolatedEPowerButtonEvent = Mask (Send/Do not & Accept/Dismiss Isolated Environment shutdown) - if the flag Do Not Send is present, then the ACPI event won't get inside the Contained Environment's Angelic Bus or VME's ACPI device emulation.

### Performance and optimization

#### System startup auto-performance scoring

At each start-up, SL Application must score the available resources and execute a performance test if the configuration is known to be different from the latest start-up.
Proper tactics and vectors of optimization must be established according to the available CPU & GPU flops, RAM, VRAM and persistent memory.

#### Memory Health Service

System will perform scheduled performance checks on physical memory modules (RAM, VRAM, CXL after basic start-up, persistent media drives after full) and non-scheduled passive diagnostics from VMM and FSOS and S.M.A.R.T reports of SSD/NVME/HDD/USB drive(s) and drive internal heat sensor data.

Service is required to warn user(s) about bad internal/removable media state and caution them before the drive(s) will enter the time period when data degradation or device failure may occur.
Second target of this service is to provide performance diagnostics information for System Menu Settings to avise proper configuration of memory tiering and the same during the OS initial installation.

#### Memory tiering

Persistent and RAM memories must be tiered, from fastest to lowest, and when needed - used in tandem or hierarchically.
To achieve so, on system installation and later - in system drives configuration, OS must have menu to configure the RAIDs and memory access paradigm.

**Hierarchically**
Slow storage HDD <-> faster storage SSD <-> fastest, RAM as a storage
When program unloads, it saves the associated RAM DS space into the SSD/HDD drive, then when pc turns down or when the DataTime event arrives, the faster drive(s) writes data to the slower one(s).
RAM DS behavior should be also configurable

**Tandem**
Slow storage HDD - persistent memory
Fast storage SSD - cache
RAM - for cache of HDD/SSD or for fast file access and then write or for cache (configurable)

**Standard**
No memory interconnections established apart from usual RAIDs or back-up drives.

Any of the two schemes is not colliding with the ability to set-up a back-up drive.
While tiering and optimization is good, data integrity is no less important - logic of storing FileSystem objects in faster memory before writing them to the slower, must not be applied to removable media, in order to avoid data corruption and user confusion.
If the RAM amount is insufficient to work with partitions using RAM DS, auto-tiering will suggest disabling the RAM DS.

#### FileSystem Orchestration Service (FSOS)
_**Core OS Application**_

FSOS is all-in-one service to provide interaction layer betwen apps and FileSystem I/O operations, it itself doesn't provide FS Driver logic, instead it interacts with the available candidates and orchestrates them.
FSOS must incorporate in itself the principles of how Zettabyte File System work, RAM DS support and more importantly - hash check practices (if the selected FS doesn't support the Hash in inode/file metadata, then FSOS must store it in DB file on partition related)

FSOS must have user-defined (on machine's administartor privelegies level if it touches the internal storage medias) configuration, which will specify:

1. ZFS behavior (on/off)
2. ZFS behavior Provenance Chains (on/off)
3. ZeroCopy unification - same content hash but different metadata into the same physical data on drive, referenced with a different filelink object, which will behave exactly like the real file, and the real one will be deleted only if all references to it will.
4. Whether to Strip away file's metadata from file format (within file's contents) and move it to the appropriate FSOS DB file / FileSystem's own meta-tag registry (if supported)
5. Prohibit existence of 2 files with the same hash within the same physical media partitions or not
6. RAM DS settings & configuration
7. Memory tiers & RAIDs configuration
8. MHS reporting (on/off)
9. Prove collection policy: MASK {content, metadata, FileSystem location}
   
 Cryptvault Password Provider Service or Password Manager based encryption process must take place before the unification or prohibition process.

 Encrypted folders support - files inside folder must not be readable before the decryption and must be marked as encrypted, if FS supports - then inode encryption will take place (the Folder's Name will be encrypted too and not shown until the encryption key for it is active)

 Angelic Bus (Event Controller) support for all FileSystem events.

 Compatibility provisioning of Memory Health Service, supplying it with mundane operation statistics such as what was the data write and data read speeds during every operation

 If the FSOS is operating with files inside the RAM DS situation, the hashing routine must occur before writing to the lower level drive, operating ZFS semi-uniformely between drives, keeping the logic that the non-persistent memory devices are not suitable to house the _only_ copy of the file, and thus unification with unwritable or non-persistent media **must NOT occur** too.

The optimizatory logic of stripping away the metadata must also apply when the file write is executed, to avoid re-writing or scanning file when only its metadata was edited, for such a fast pattern scan must occur before the further operations
Blank files must do not undergo hashing process and skipped instead, if the filelink pointing to the NULL (not a deprecated or unexisting pointer in the FileSystem, but literal blank) it is considered to point to empty file, so if the metadata is present, the only information to be gained is metadata.
If FSOS detects that application never goes into analyzing proper file's metadata before loading it, it will support edited file version with metadata placed in respectible alignment (detection algorithm is simple: the file read request occurs, but file FS metadata read event didn't occur)

Inodes of the encrypted files do not undergo hashing or plain indexing procedures, they are protected, so if the file is to be encrypted, the content will get hashed AFTER the encryption procedure and do not participate in ZFS-like deduplication pool.

OS Core Binaries and System Critical Files is also opted out from deduplication procedures.
FSOS must provide API for user or an appliaction to exclude files from deduplication pool manually.

##### Hash collision avoidance
To mitigate hash collisions, hash per file is stored as two parts:
1. Datasize - size of the content hashed
2. Hash of the content itself

##### Deduction Workflow: Provenance Chain

To supply user with ability to track File acquisition and editing history, FSOS realizes Data Provenance Chain (DPC).

1. DPC Journal
 DPC Journal is collection of actions (Proves) done with the specific file (connected to its instance (filelink) if the FS is under ZeroCopy protocol), its {content, metadata, FileSystem location} change by applications, stored in the associated with the file special inode metadata section (if FIleSystem Driver supports) or DataBase associated with the FileSystem Partition in which file information is stored.
2. Prove
   When the application accesses File Descriptor, FSOS takes a note, timestamping the event for later Prove generation, if the changes was done.
   If the changes between previous file version and new file version exists, FSOS generates an Prove:
   * Procedure start timestamp
   * Procedure completion timestamp
   * Application fingerprint: application identifier, process Handle_ID, CPPS.Sign() for the Prove (provided by the application adressing the FSOS)
   * User fingerprint: UID and CPPS.Sign() for the Prove
   * Source (HoDAP):
     ```
     NetworkDevice0, TCP https://github.com/ibotpeaches/APKTOOL/Readme.MD
     ```
     Prove generation can be triggered by events specified in Prove collection policy.
     Directories and files can be forcefully included or excluded from DPC generation.
3. Adrift protection
    To protect the versioning histories from adrift, they are stored in secure vaults accessible only by FSOS or associated FSD(FileSystem Driver), if the endtarget of operation is not the first file itself, but a ZeroCopy protocol's filelink object, then, just like a metadata, the DPC will be stored in it instead of the file content source.
4. Provenance Tree
   FSOS.RequestProvenanceTree( FILE_DESCRIPTOR ) will return the Proves for current and previous file versions, tying all together.

#### Ext5 FileSystem Driver (Ext5FSD)
_**Core OS Application**_

Ext5 is main FileSystem Format recommended to use within SyeOS.
Ext5 filesystem must incorporate in itself the principles of how Ext4 stores data and per-file metadata storage in inodes to be able to specify the tags, categories, score & etc not in the file itself, but within the FileSystem, agnostically to the file type, such method must have isolated compartment for file's hash, which cannot be altered through user tools, but indeed will be assigned only by the OS Ext5 FSD.
The hash info (datasize-hash pair), thus must be stored in separate section from the file's metadata, in case if any user want to add a "hash" as a name for meta tag.
Such meta tags may be used by users to add notes to their files, so Ext5 must have support for file links inside metadata to make files associatable to each another.
Encrypted folders support - inodes within encrypted sections must not be readable before the decryption and must be marked as encrypted.
Ext5 also provide support for DPC storage.

 #### RAM Drive Service (RAM DS)
 _**Core OS Application**_
 
 A simple driver providing ability to store files in RAM (thjs service's memory), imitating the physical media device I/O channel.
 
#### VMM

To speed up the overall system performance, its own Virtual Memory Manager must support statistics collection and different application & library loading practices.
Statistic about methods/data at which memory adresses used must be collected internally, on the session basis (start-to-finish) and the average for the whole history of app/library use.
 
 ##### Binary file loading methods

Memory adresses, found to be not used often or at all, will load into real physical RAM based on the load method selected:
Cold Load:
Only part of the application/library will be loaded into the memory, and only on Segfault caused by the loading practice, VMM will trigger OS to load the missing content, to which the process afressed unsuccesfully.

Hot Load:
All of the library/application will be loaded into the memory.

 ##### RAM re-population cycle avoidance

 For specified by the OS administrator application and OS Core Applications, if the option to write and request from multiple memory banks is present, then it should do such way, filing a Hedged Requests and returning to the execution context only the data, that was received the fastest, denying or ignoring the further responds on RAM queries.

 Also relays information about latencies, real speeds and segfault events to Memory Health Service.

 #### Application File Access Optimization (AFAO)
 
 In the same manner, as VMM behaves with RAM memory fragments, some service in the OS [most likely task manager] must behave with task's files, while keeping the note in which container context the app was executed and omitting analysis of unsufficient files to monitor.
 The monitoring heuristics must analyze relation of read speed required (and how much application stales from the hikkups) - if the read rate is sufficient enough to make no real operational difference (measured by throughput from the program's inputting "HoDAP pipe" to the outputting "HoDAP pipe" either it be other file, data stream [audio for example] or pixel matrix; graphics drawing performance is measured by the fps metrics, for se).
 (let's say less than 10mb by default; configurable.) while also monitoring the read/write rate required by the application's process;
 
 If the file is being written too fast and application stales between write operations, they need to be dealt with the new way apart from Hold and Cold loads -> Tempered Write (part by part to virtual RAM DS input stream, then to real physical memory);
 If the file is being re-written too often and it will probably damage the TBW limit sufficient enough to be concerned (not a log file, required to be appended everytime, but something like browser cache) - it must be treated as a high data corruption risk and undergo Cold Write process: stored in RAM DS until the application finishes its work or Date-Time event occurs (time passes by long enough) - {WriteOnFinish, WritePerInterval X and WriteOnFinish}.
 Otherwise, the usual (Hot Write) procedure will be assigned - file will be written when the program need so.
 User may also specify the proper approach manually.

Cold Load:
Files will be loaded when app requests them to be

Hot Load:
If the RAM DS or Dynamic RAM DS (without fixed size) is enabled, then Hot Load is possible.
Files specified by user or often loaded by the application will be loaded into RAM DS hook at the application startup, to avoid hikkups whenever the application unloads or loads them, such file could be sound libraries for MIDI-based and Studio Work, game assets, software emulation libraries, etc.

#### Meta-libs (meta-libraries) as compatibility layer

UNIX and Linux based OS known for having one particular issue - if the dependancy of certain application is updated, and it is not stated within the application that new version is supported, the application package will got uninstalled or at least won't be run by OS, SyeOS's response to that is using Meta-lib headers to adapt newer version of libraries to older calling and interaction behavior, adapting the incoming data to pass through proper sequences for newer versions, instead of keeping multiple versions of libraries or deprecating the application entirely.

#### VM raw stream

Integrating HoDAP & FS hooks into VME yields ability to directly bridge hardware to VM [for example, drive containing OS]

### Configuration

Every configuration is derived from the Parent one, if nothing new stated then the Parental configs apply, however ACL and CCL do not share this "inheritance" logic - limitations can be only hardened, not freed up, but they do not come from unathorized providing.

#### Containers, Workspaces

##### Container

Container is an execution containment context rolled into an OS Data Abstract Class.
It is a set of process's configuration stack - from ACL & CCL, VMM, AFAO parameters to set of inner application configurations appointed to specific application's instance.
Specific HIDs can be assigned to Container, to support isolated & multi-HID input.

##### Workspace

Workspace is a hierarchical supremitive of Container, a set of a specific to it rules and parameters to run programs, in pair with its own Work Screen (instead of so-called Virtual Desktop), thus the Work Screen provider is the same application providing the Workspace functionality itself, interacting with MUIPS, ACL/CCL/AP management, app configuration and requesting Core OS Apps to provide certain access to hardware, Core OS Application or System Level Application.
Workspace parameters can define its containment level, from none all the way up to VME, with its own method to use & re-use containment layouts, such the way that structure similar to A.H.I.T environments can be re-used by user for different targets.
Apart from just the conceptual weights, a proper Workspace must have its own WorkScreen - a set layour of applications used as the main interaction environment for Workspace [=not dictated it to be for usual Visual Interfaces only] it defines a set of apps, their relations and processes environment; for visual applications such apps can be File Navigator, Virtual Machine Viewport, Text Editors, Local NotebookLM Window, Music Player, Taskbar, etc; For the non-visual it may be audio assistant, item categorizer or even network router, network server, device data stream listener, etc.
Configuration of Workspace must provide a way to execute certain appointed by user actions when specified event occurs -  an [Angelic Bus, Listener.EndPoint]
Configuration of Workspace may also contain lists of appointments for metafied SyeOS-native apps, such lists will be:
1. Selected Metafied UI layouts for applications
2. So-called "Meta-apps" layout list [refer to Configuration logic, Meta-apps]

##### Workspace Events
Workspace Load
Workspace Unload
Workspace Switch {In, Out}
Workspace {Display, HID} Assigned
Workspace {Display, HID} UnAssigned
Workspcae {Display, HID} Switched
WorkScreen {Focus, UnFocus}. 

##### WorkScreen Layout
Every WorkScreen can have its own layout, selecting the main Desktop provider application (can be any), and instead of Widgets - other applications, atop (with other Z indexes) or at side of the main application, aligned to themselves, fixed, unified by splitview mode or tileswitch mode.
Default Desktop application is File Navigator, displaying the assigned path to the Workspace's Desktop Folder in FileSystem.
Creating a new instance of the same Workspace Layout just creates a new WorkScreen for it, if the WorkSpace do not have **Isolated** flag

#### Window Manager
Window Manager must support Window Frame&Style confguration in the manner:
Use Execution Context's Theme (Boolean)
Custom Theme File (FileSystem Path)
Window Auto-Anchor after nearing to other with Auto-Anchor (Boolean)
Window Capture HID (Boolean)
Window Type (Int)
Window Border Count (Int)
Window Border Width (Int)
Window Border Orientations [] (Degree from 0° to 180°) - as example 0°, 45°, 90°, 135°, 180° is Top, Right, Bottom, Left positions for rectangular Window Frames;
Window Border positions will be derived from the known supplied Application Content Boundaries and the current size of Applcation Window.
Window Border's Control Elements Alignment - Alignment (Left, Center, Right)
Window Border's Control Element Rotation - will determine the rotation of the line of the elements, as they can be vertically displayed even when the Border is itself in horizontal position in relation to the Window.
Window Border's Control Elements - Set [] of elements to display on the Border surface the property is applied to;
Possible Elements are: label, button, regulator (enable/disable + limitation slider)

0. Close
1. Maximize/Minimize
2. Maximize/Minimize Horizontally
3. Maximize/Minimize Vertically
4. Fold Up/Unfold
5. Hide to Current Window/Task list
6. Pin/Unpin
7. Enter Fullscreen Mode
8. Scaling Lock/Unlock
9. Move Window
10. Open System Settings Menu for Application
11. Open Window Manager Menu for Application
12. Positioning Menu Opener (Menu: Window WorkScreen Anchoring, Windows Splitview/Related Layout assigner, Window Transparency, Window Z-order pin (Dynamic/Integer (fixed)/AlwaysAtBottom/AlwaysAtTop))
13. Freeze/UnFreeze Process
14. Open/Hide In-Window Search Bar
15. Display Process's Console Log/Display Process's Window
16. Throw to the next Workspace/Screen
17. Throw to the previous Workspace/Screen
18. Throw to the upper Workspace/Screen
19. Throw to the bottom Workspace/Screen
20. Show/Do Not Show Notifications
21. Sound Level Control
22. Sound present/mute
23. Take screenshot
24. Record video Start/Pause/Stop
25. Record audio Start/Pause/Stop
26. Screen record prohibit on/off
27. Audio record prohibit on/off
28. VNC transmission on/off
29. Mic switch on/off
30. Network switch on/off
31. Bluetooth switch on/off
32. RAM Graph
33. VRAM Graph
34. CPU Graph
35. GPU Graph
36. Storage Graph
37. Audio Dbs Graph
38. Bluetooth Activity Graph
39. Network Activity Graph
40. Thermodynamical Efficacy Coefficient Graph
41. RAM Usage Label
42. VRAM Usage Label
43. CPU Usage Label
44. GPU Usage Label
45. Storage Usage Label
46. Audio Dbs Label
47. Bluetooth Usage Label
48. Network Usage Label
49. Thermodynamical Efficacy Coefficient  Label

#### Meta-app
Meta application is type of application constructed by specifying Meta-app layout, determining the required APs, set of required apps/framework apps, their CCL & HoDAP interaction layout and if needed - their unified Metafied UI layout file or/and their respectible application windows layout.
After creating a proper Meta-app layout it can be installed locally or globally as a ULApp package.

_Meta-app layouting can be used to construct IDEs from Code Editor, File Navigator, Compiler and Graphical Debugger applications._
#### Section about Scriema (analog for Javascript & JSON -> Poetic Script Language [Script + Poema -> Scriema, *.scp or *.scie file extension] )
### Section about UX & UI
#### Section about Metafied UI
##### Section about Need to distinguish apps/workflows separate in order to induce warning about their operational context or workflow difference
#### Section about Process clustering, splitview and WM

### Section about Apps
#### Section about Workspace & WorkScreen Layout Editor
#### Section about Meta-app layout editor
#### Section about Metafied UI editor
#### Section about Cryptvault Configurator
#### Section about Keyring (Password Manager)
#### Section about File Navigator
##### Access Policies and ACL logic
File Navigator has access only to reading only a limited count of files - those, created by File Navigator itself and those appointed to it.
Soecial FSOS permission, allowing File Navigator to read .fnavlist is applied when the Re-Fold practices are required or by clicking the file inside File Navigator, so the OS will ask user to allow File Navigator read the file or not.
For the Execution Container's scope of FileSystem visibility, File Navigator can see only the list of files and directories, their meta-tags, hashes and paperclicps provided by FSOS.
File previews, icons and such must be provided from a separate indexing service (a FSOS subservice).
When the file is opened from File Navigator, a signal to open applcation or file in a new application is routed to the closest Container App Calling/Execution Manager (usually Workspace host), to the program only File Descriptor is passed into a respectible launch parameter or a HoDAP, if the application doesn't have access to the File Descriptor, user will be prompted to grant the access permission (for one launch, for counted time or indefinetely).

##### Re-Fold View
_Just another headwrap about pseudo-navigation_

User-defined re-organization of contained in directory(directories) files and directories into alternative list representation, such representations can be then saved or read from .fnavlist files.

##### Metadata Re-Fold
Function to organize the content of directory or/and subdirectories into pseudo-folders, dedicated to the metadata tag selected for representation.

#### Section about package, layout stores and such
#### Section about metrics overview apps
#### Section about built-in Notebook app
#### Section about optional local search engine like relloc
#### Section about optional local NootebookLM
#### Section about deductive environment app

### Section about Setup sequence in OS installer and user x/i of it
To mitigate Digital Data Dark Age, SyeOS installers for non-specific hardware must all supply with all of the system packages intact, just keeping the targeted configuration as main selection for installation process.
Binaries must be built during the installation process from the source files, confirming that the only applications which could've been contamined is the installer bootloader, installer itself and compiler.
To optimize code execution further, compiler flags for support of CPU-specific instructions will be embedded into build configuration, so that the any program will gain as much benefit from hardware configuration as it can.

Conclusion: if you think hard enough, all of the UI of SyeOS could be drawn inside a Console Shell...