# Evaluativa-3
puestos = ["ceo","Desaroollador", "Analista de datos"]
empleados = []


def registro_de_empleados(empleados):
    nombre_empleado = input ("Ingrese el nombre y el apellido del trabajador: ")
    cargo_empleado = input ("Ingrese el cargo del trabajador: ").lower()
    while cargo_empleado not in puestos:
        print("Cargo no existe, intente nuevamente")
        cargo_empleado = input ("Ingrese el cargo del trabajador: ").lower()
    sueldo_bruto = int(input ("Ingrese la sueldo bruta del trabajador: "))
    descuento_salud = sueldo_bruto * 0.07
    descuento_afp = sueldo_bruto * 0.12
    liquido_pagar = sueldo_bruto - descuento_salud - descuento_afp

    empleados.append ({
        'nombre': nombre_empleado,
        'cargo': cargo_empleado,
        'sueldo_bruto': sueldo_bruto,
        'descuento_salud': descuento_salud,
        'descuento_afp': descuento_afp,
        'liquido_pagar': liquido_pagar
    })

def listar_empleados(empleados):
    print("Lista de empleados")
    for empleado in empleados:
        print(empleado)
def imprimir_planilla(empleados):
    cargo_seleccionado = input ("Ingrese el cargo para imprimir la planilla o bien presione ENTER para seleccionar todos: ")
    if cargo_seleccionado == "":
        archivo_planilla = "planilla_todos.txt"
        print ("Planilla de todos los empleados")
        print(archivo_planilla)
    elif cargo_seleccionado in puestos:
        archivo_planilla = f"planilla_{cargo_seleccionado}.txt"
        print(f"Planilla de {cargo_seleccionado}")
        print(archivo_planilla)
    else:
        print ("Cargo no existe, intente nuevamente")
        return

    with open (archivo_planilla, "w") as archivo:
        for empleado in empleados:
            archivo.write(f"nombre y apellido: {empleado['nombre']}\n")

menu ="1. Registrar empleado\n2. Listar empleados\n3. Imprimir planilla\n4. Salir\n"


while True:

    print(menu)
    eleccion = int(input(" Bienvenido, Ingrese su eleccion para comenzar: "))
    
    if eleccion == 1:
        registro_de_empleados(empleados)
    elif eleccion == 2:
        listar_empleados(empleados)
    elif eleccion == 3:
        imprimir_planilla(empleados)
    elif eleccion == 4:
        break
    else:
        print("Opcion no valida, intente nuevamente")
