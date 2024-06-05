// AsistenciaLaboral.js

class AsistenciaLaboral {
    constructor() {
        this.empleados = {};
    }

    registrarEmpleado(id, nombre) {
        if (this.empleados[id]) {
            console.log(El empleado con ID ${id} ya está registrado.);
            return;
        }
        this.empleados[id] = { nombre, registros: [] };
        console.log(Empleado ${nombre} registrado con éxito.);
    }

    registrarEntrada(id) {
        const empleado = this.empleados[id];
        if (!empleado) {
            console.log(Empleado con ID ${id} no encontrado.);
            return;
        }
        const now = new Date();
        empleado.registros.push({ tipo: 'entrada', tiempo: now });
        console.log(Entrada registrada para ${empleado.nombre} a las ${now}.);
    }

    registrarSalida(id) {
        const empleado = this.empleados[id];
        if (!empleado) {
            console.log(Empleado con ID ${id} no encontrado.);
            return;
        }
        const now = new Date();
        empleado.registros.push({ tipo: 'salida', tiempo: now });
        console.log(Salida registrada para ${empleado.nombre} a las ${now}.);
    }

    generarReporte(id) {
        const empleado = this.empleados[id];
        if (!empleado) {
            console.log(Empleado con ID ${id} no encontrado.);
            return;
        }
        console.log(Reporte de asistencia para ${empleado.nombre}:);
        empleado.registros.forEach(registro => {
            console.log(${registro.tipo} - ${registro.tiempo});
        });
    }
}

// Ejemplo de uso
const asistencia = new AsistenciaLaboral();
asistencia.registrarEmpleado(1, 'Juan Perez');
asistencia.registrarEntrada(1);
setTimeout(() => {
    asistencia.registrarSalida(1);
    asistencia.generarReporte(1);
}, 2000);

asistencia.registrarEmpleado(2, 'Ana Gomez');
asistencia.registrarEntrada(2);
setTimeout(() => {
    asistencia.registrarSalida(2);
    asistencia.generarReporte(2);
}, 4000);
