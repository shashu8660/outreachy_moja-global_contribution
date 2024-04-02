# How to install FLINT on your local system:
# Windows Installation:
**Prerequisites before installing FLINT:**

GitHub
Visual Studio
CMake
Docker
These four are required for your journey of contribution towards moja-global. It's better to install them before cloning FLINT.

Now that you have all the necessary prerequisites, you can proceed with the Installation.

**First, we install VCPKG:**
Using VCPKG, we can install the required libraries.

Open GitHub on your system and search for moja-global. Then in the moja-global repo (repository), search for the VCPKG repo. In the VCPKG repo, copy the URL of the repo: https://github.com/moja-global/vcpkg.git

After copying the VCPKG URL, you need to create a folder to hold the moja-global project.

So open File Manager and create a folder named "Development" on your local desk.

Note: Create the folder name exactly as "Development" or you might encounter issues while installing FLINT. For example, all paths used below with "C:\Development\moja-global" need to be modified to match your system's build location of the moja project.

After creating the "Development" folder, create a sub-folder named "moja-global" in the "Development" folder.

*Then open the moja-global directory in the command prompt (cmd). Make sure you're in the moja-global directory, then clone the VCPKG repo in the moja-global folder using the following command:*

git clone https://github.com/moja-global/vcpkg.git
This clones the VCPKG into the moja-global folder.

**After that, direct the directory to VCPKG in your command prompt by using:**

```bash
cd vcpkg
```
**To install all files of VCPKG, use the following commands:**

```bash
bootstrap-vcpkg.bat
```

**Wait until it runs successfully. Then install packages using the following commands:**

```bash
vcpkg.exe install boost-test:x64-windows boost-program-options:x64-windows boost-log:x64-windows turtle:x64-windows zipper:x64-windows poco:x64-windows libpq:x64-windows gdal:x64-windows sqlite3:x64-windows boost-ublas:x64-windows fmt:x64-windows libpqxx:x64-windows
```

*Note: It might take up to 1 hour to install all the packages depending on your system's speed.*

**After successfully installing packages in the VCPKG folder, redirect the directory to moja-global in your command prompt by using:**

```bash
cd..
```
*Then open the moja-global repo on GitHub and search for the FLINT repo in it. Copy the URL of the FLINT repo: https://github.com/moja-global/FLINT.git*

**Then clone the repo in the moja-global folder by command prompt using:**

*git clone https://github.com/moja-global/FLINT.git*

After cloning the FLINT repository, switch to the develop branch. Start cmd in the FLINT folder of your system and run the command:

```bash
cd Flint
git checkout develop
```

**Using CMake to build the project:**

Start cmd in your FLINT core repository folder. Now use the following commands to create the Visual Studio solution:

By changing the directory to source in cmd and creating a new folder build in the source folder by using:

# Create a build folder under the Source folder

```bash
cd source
mkdir build
cd build
```

**Now create the Visual Studio Solution (2019):**

```bash
cmake -G "Visual Studio 16 2019" -DCMAKE_INSTALL_PREFIX=..\..\.. -DVCPKG_TARGET_TRIPLET=x64-windows -DENABLE_TESTS=OFF -DENABLE_MOJA.MODULES.ZIPPER=OFF -DCMAKE_TOOLCHAIN_FILE=..\..\..\vcpkg\scripts\buildsystems\vcpkg.cmake ..
```

Run this line successfully in cmd.

# Building the FLINT:

- Type "moja.sln" in the command prompt. Visual Studio is launched.

	moja.sln

- After Visual Studio has loaded completely, move to the Solution Explorer in the top right, expand the 'CMakePredefinedTargets' and select 'ALL_BUILD'.

- Right-click on 'ALL_BUILD' and click on 'Build' in the menu.

- If the output says "Build 7 succeeded" as shown in the image below, FLINT has built successfully.

**To see the freshly compiled FLINT executable, open the build folder and in the command prompt type:**

```bash
cd bin\debug
```

Type "moja.cli" in the command prompt:

```bash
moja.cli
```

*You see the output as:*

```bash
moja.cli version.
general option.
command-line only option.
configuration file option.
```

If your output has them all then the installation was successful.

# **Flint.example Installation:**

**-Flint.example:**

**For installing Flint.example:**

*First Environment: Visual Studio:*

In the Visual Studio environment option for setting up 'Flint.example' , the options to run, develop, and debug the repository code are available.

For Flint.example to run, all VCPKG packages should be present in the moja-global folder.

*First go to the moja-global repo on GitHub then search for flint.example. Then in flint.example repo copy the URL of flint.example: https://github.com/moja-global/FLINT.Example.git*

**Then in cmd direct toward the moja-global dir then run cmd:**

*git clone https://github.com/moja-global/FLINT.Example.git*

*To clone the Flint.example in your moja-global folder.*

**Next step is to build the Flint.example:**

*In the cmd direct dir to Flint.example by:*

```bash
cd flint.example
```

**Create a build folder under the Source folder:**

```bash
cd source
mkdir build 
cd build
```

*Next step is to choose which type of simulation you want to execute.*

**You may run one of the following generate commands:**

**Commands to run cmake for the point simulations:**

```bash
# Generate the project files
cmake -G "Visual Studio 16 2019" -DCMAKE_INSTALL_PREFIX=C:\Development\Software\moja -DVCPKG_TARGET_TRIPLET=x64-windows -DOPENSSL_ROOT_DIR=c:\Development\moja-global\vcpkg\installed\x64-windows -DENABLE_TESTS=OFF -DCMAKE_TOOLCHAIN_FILE=c:\Development\moja-global\vcpkg\scripts\buildsystems\vcpkg.cmake ..
```
**Commands to run cmake for the spatial simulations:**

```bash
# if you're planning to run spatial chapman richards example you also need to enable the gdal module
# Generate the project files
cmake -G "Visual Studio 16 2019" -DCMAKE_INSTALL_PREFIX=C:\Development\Software\moja -DVCPKG_TARGET_TRIPLET=x64-windows -DOPENSSL_ROOT_DIR=c:\Development\moja-global\vcpkg\installed\x64-windows -DENABLE_TESTS=OFF -DENABLE_MOJA.MODULES.GDAL=ON -DCMAKE_TOOLCHAIN_FILE=c:\Development\moja-global\vcpkg\scripts\buildsystems\vcpkg.cmake ..
```

*First let's try the point simulations:*

**In cmd:**

```bash
cmake -G "Visual Studio 16 2019" -DCMAKE_INSTALL_PREFIX=C:\Development\Software\moja -DVCPKG_TARGET_TRIPLET=x64-windows -DOPENSSL_ROOT_DIR=c:\Development\moja-global\vcpkg\installed\x64-windows -DENABLE_TESTS=OFF -DCMAKE_TOOLCHAIN_FILE=c:\Development\moja-global\vcpkg\scripts\buildsystems\vcpkg.cmake ..
```

*Run it successfully.*

*There are two models to test Flint.example which are:*

**RothC example**
**Chapman Richards example**

*First let's try RothC example:*

- We also have a RothC example for point level simulations. In order to run this example, you may modify the following arguments in the above test settings command arguments. These arguments will point at the right configuration files for RothC. Please follow the following steps to set the correct configuration -

*Get to 'flint.example' folder from the 'moja-global' folder then in flint.example open 'source' folder then open 'build' folder from source search for 'flint.example.sln'. Open the 'flint.example.sln' in visual studio*

- Build the debug configuration ALL_BUILD target by right-clicking the 'ALL_BUILD' node and selecting 'Build'.

*After Build the debug configuration All_BUILD.*

- Then right-click the the 'moja.flint.example.rothc' node and select 'Set as Startup Project' then right-click again and select 'properties'. Navigate to Configuration 'Properties/Debugging' properties and configure the following:

**First in command edit by click at arrow at right side of the command press edit and edit as:**

```bash
Command:

C:\Development\moja-global\FLINT\Source\build\bin\Debug\moja.cli.exe
```

*Next, command arguments:*

**Command Arguments:**

```bash
--config config\point_rothc_example.json --config config\debug\libs.base_rothc.win.json --logging_config logging.debug_on.conf
```

*Next, edit the working directory:*

**Working Directory:**

```bash
$(SolutionDir)..\..\Run_Env
```

*Next, edit the environment:*

**Environment:**

```bash
PATH=C:\Development\moja-global\vcpkg\installed\x64-windows\debug\bin;C:\Development\moja-global\FLINT\Source\build\bin\$(Configuration);%PATH%
LOCAL_LIBS=$(OutDir)
MOJA_LIBS=C:\Development\moja-global\FLINT\Source\build\bin\$(Configuration)
```

*After that, apply the change and press OK.*

You should now be able to select Debug -> Start Debugging to start a debug run of the RothC example.

*Now you can run the RothC example.*

**Instructions for Chapmans Richards Example:**

*Before running the Chapmans Richards example, we need to set up GDAL.*

**Enable moja.modules.GDAL:**

- Before moving on to setting up the Chapman Richards model, we need to enable the 'moja.modules.GDAL' flags. We can toggle these flags by clicking on 'BROWSE BUILD' and setting it to the build directory where we just built the solution.

*Open the solution that CMake created at C:\Development\moja-global\FLINT\Source\build\moja.sln.*

**Check the following flags present:**

- ENABLE_MOJA.MODULES.GDAL
- ENABLE_MOJA.MODULES.LIBPQ
- ENABLE_MOJA.MODULES.POCO
- ENABLE_MOJA.MODULES.ZIPPER

*Then click on configure option twice.*

*Click on 'Generate' and then you may explore all the enabled modules in Solution Explorer by clicking on 'Open Project'.*

The its opens visual studio then.

*Open 'CMakePredefinedTargets', right click on 'ALL_BUILD' and click on 'Build'.*

**Then open environment variables and click on new in the System variables**

*And add "GDAL_DATA" (all in caps) in path add GDAL path from vcpkg ':C:\Development\moja-global\vcpkg\installed\x64-windows\share\gdal'*

*Now we are ready to run Chapmans Richards example*

**Chapmans Richards Example:**

Based on the moja global repository Chapman Richards, this sample can be run on both point and spatial versions (over Dominica)

- Get to 'flint.example' folder from the 'moja-global' folder then in flint.example open 'source' folder then open 'build' folder from source search for 'flint.example.sln'. Open the 'flint.example.sln' in visual studio

- Then right click the the 'moja.flint.example.Chapmans' node and select 'Set as Startup Project' then right click again and select 'properties'.

- Navigate to Configuration 'Properties/Debugging' properties and configure the following:

**Edit Command:**

*First, in the command edit, click on the arrow at the right side of the command, then press edit:*

**Command:** 

```bash
C:\Development\moja-global\FLINT\Source\build\bin\$(Configuration)\moja.cli.exe
```

*Edit Command Arguments:*

**Command Arguments (Point Version):**

```bash
--config config/point_forest_config.json --config config/$(Configuration)/libs.gdal.chaprich.win.json
```

**Command Arguments (Spatial Version):**

```bash
--config config/forest_config.json --config config/$(Configuration)/libs.gdal.chaprich.win.json --config_provider config/forest_provider.json
```

*Edit Working Directory:*

**Working Directory:**

```bash
 $(SolutionDir)\..\..\Run_Env
 ```

*Edit Environment:*

**Environment:**

```bash
PATH=C:\Development\moja-global\vcpkg\installed\x64-windows\bin;C:\Development\moja-global\FLINT\Source\build\bin\$(Configuration);%PATH%
LOCAL_LIBS=$(OutDir)
MOJA_LIBS=C:\Development\moja-global\FLINT\Source\build\bin\$(Configuration)
```

*After making these changes, apply the changes and press OK.*

- You should now be able to select Debug -> Start Debugging to start a debug run of the Chapmans Richards example.

*Now you can run the Chapmans Richards example.*

**Next and last step is to Setup Docker Containers.**

**Setup Docker Container:**

- Containers are a simple way to build FLINT and all required dependencies.

**Building using Prebuilt Image:**

Instead of building the required libraries, pre-built Docker Image is available for FLINT at our GitHub Container Registry. You can pull and run FLINT using this prebuilt image using the following commands:

**Pull the image:**

```bash
docker pull ghcr.io/moja-global/flint.example:master
```

**Run a container:**

```bash
docker run --rm -ti ghcr.io/moja-global/flint.example:master bash
```

**Run CLI:**

```bash
moja.cli --help
```

*That's all! Thank you for going through the installation process. If anything is missing, I would like to get feedback.*