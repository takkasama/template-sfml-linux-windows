# SFML C++ Template — Linux & Windows

![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![SFML](https://img.shields.io/badge/SFML-2.x-77B900?style=flat-square)
![Linux](https://img.shields.io/badge/Linux-supported-FCC624?style=flat-square&logo=linux&logoColor=black)
![Windows](https://img.shields.io/badge/Windows-supported-0078D4?style=flat-square&logo=windows&logoColor=white)

A reusable **C++ and SFML project template for Linux and Windows**, configured for the **ZinjaI IDE**. It provides separate Debug and Release build configurations and a small graphics example to help you start building multimedia applications.

> **Note:** This is a **ZinjaI (`.zpr`) project**, not a CMake project. Compiler, SFML library paths, and linking settings may need adjustment for your operating system and toolchain.

## Technologies

| Technology | Purpose |
| --- | --- |
| C++ | Application development |
| [SFML](https://www.sfml-dev.org/) | Graphics, windowing, audio, network and system modules |
| [ZinjaI](https://zinjai.sourceforge.net/) | IDE and project/build configuration |
| GCC / MinGW | Native C++ compilation |
| Linux / Windows | Target operating systems |

## Features

- ZinjaI project file (`template-sfml-windows-linux.zpr`).
- **Debug** and **Release** configurations for Linux and Windows.
- Links to the SFML graphics, window, audio, network and system modules.
- Example that opens a window, loads `sfml.png` and draws a sprite.
- Separate Linux and Windows SFML directories included in the repository.

## Repository Structure

```text
.
├── main.cpp
├── sfml.png
├── template-sfml-windows-linux.zpr
├── SFML-linux/
├── SFML-windows/
├── Release_Linux/
├── Leeme.txt
└── README.md
```

The `Release_Linux/` folder is included in the repository. The `Debug_*` and `Release_*` directories may also be used as build output directories by ZinjaI.

## Getting Started

### 1. Create a Project

Use **[Use this template](https://github.com/takkasama/template-sfml-linux-windows/generate)** on GitHub, or clone the repository:

```bash
git clone https://github.com/takkasama/template-sfml-linux-windows.git
cd template-sfml-linux-windows
```

### 2. Open in ZinjaI

Open `template-sfml-windows-linux.zpr` in ZinjaI. Choose the build configuration appropriate for your platform:

| Configuration | Operating system | Build type |
| --- | --- | --- |
| `Debug_Linux` | Linux | Debug |
| `Release_Linux` | Linux | Release |
| `Debug_Win32` | Windows | Debug |
| `Release_Win32` | Windows | Release |

The selected configuration controls compiler/linker options and the executable's output location.

### 3. Linux Setup

Install a C++ compiler, the required build tools and SFML development libraries. For example:

**Arch Linux:**

```bash
sudo pacman -S --needed base-devel sfml
```

**Debian / Ubuntu:**

```bash
sudo apt update
sudo apt install build-essential libsfml-dev
```

The checked-in Linux configurations link against `sfml-graphics`, `sfml-audio`, `sfml-network`, `sfml-window` and `sfml-system`, using the compiler's default library search paths. If your libraries are installed elsewhere, adjust **include directories** and **library directories** in ZinjaI.

**Compatibility:** The example uses the **SFML 2.x API** (`sf::VideoMode`, `sf::Event`, `sf::Sprite::setTexture`). SFML 3 requires source changes. Check the version provided by your distribution before building.

### 4. Windows Setup

Install a **MinGW/GCC toolchain compatible with your chosen SFML build**, then configure the project in ZinjaI:

1. Select `Debug_Win32` or `Release_Win32`.
2. Set the SFML **header/include directory** and **library directory** to your installation.
3. Review the **`SFML_STATIC`** macro already present in the Windows configurations.
4. If using **static SFML libraries**, use the correct static library names and their required additional dependencies for your exact SFML/MinGW distribution.
5. If using **dynamic SFML libraries**, remove `SFML_STATIC`, link the matching import libraries, and make the required DLLs available beside the executable or on `PATH`.

The original ZinjaI configuration references `${MINGW_DIR}\\sfml2\\include`, `${MINGW_DIR}\\sfml2\\lib` and `${MINGW_DIR}\\sfml2\\bin`. These paths are **toolchain-specific**; update them if your installation uses different locations.

> **Important:** Do not mix Windows SFML binaries compiled for a different compiler, architecture, or runtime. The project settings should match the installed SFML package.

## Build and Run

In ZinjaI, select a configuration and use its **Build / Run** actions.

The Linux configurations specify output paths such as:

```text
Debug_Linux/template-sfml-windows-linux.bin
Release_Linux/template-sfml-windows-linux.bin
```

The Windows configurations specify `.exe` outputs in `Debug_Win32/` and `Release_Win32/`.

**Working directory:** The sample loads `sfml.png` through a relative path. Run it with the repository root as the working directory, or update the asset path to match your project layout.

## Example Application

The included `main.cpp` demonstrates the basic SFML rendering loop:

- Creates a 640 × 480 window.
- Loads `sfml.png` as a texture.
- Draws a sprite inside the window.
- Processes the window-close event.

This provides a simple starting point for graphics projects, small games and SFML experiments.

## Customization

1. Rename the ZinjaI project and change its output filenames.
2. Replace `main.cpp` with your application code.
3. Add graphics, sounds and other resources to your project.
4. Update build configurations when switching compiler, platform or SFML version.
5. Keep the assets accessible relative to the application's working directory.

## Troubleshooting

| Issue | What to check |
| --- | --- |
| `SFML/Graphics.hpp: No such file or directory` | SFML include directory |
| `cannot find -lsfml-graphics` | SFML library directory and linker names |
| Undefined references at link time | Library order, static/dynamic linking, missing dependencies |
| Missing DLL at startup on Windows | Required DLLs and `PATH` |
| Texture does not appear | The `sfml.png` path and working directory |
| Compilation errors with SFML 3 | The sample is written for SFML 2.x |

## Resources

- [SFML Official Website](https://www.sfml-dev.org/)
- [SFML 2.6 Tutorials](https://www.sfml-dev.org/tutorials/2.6/)
- [Project Repository](https://github.com/takkasama/template-sfml-linux-windows)

## Author

**takka-sama** — [GitHub @takkasama](https://github.com/takkasama)

---

*An SFML project foundation for C++ development with ZinjaI on Linux and Windows.*
